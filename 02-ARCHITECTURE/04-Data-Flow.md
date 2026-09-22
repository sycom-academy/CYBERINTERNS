# FinServe — Data Flow

**Classification:** Internal · **Owner:** Data Protection Officer (C. Nwosu)
**Last reviewed:** 2025-07-08 · **Next review:** annual

Where customer data originates, where it moves, who else touches it and under
what basis. This document is the reference for the record of processing
activities and for any data protection impact assessment.

---

## 1. Data categories

| # | Category | Examples | Sensitivity | Volume |
|---|---|---|---|---|
| D1 | Identity | Name, DOB, address, phone, email | Confidential | ~180,000 subjects |
| D2 | National identifiers | BVN, NIN, passport / driver's licence images | **Restricted** | ~180,000 |
| D3 | Financial | Account number, balance, transaction history | **Restricted** | ~215,000 accounts |
| D4 | Card | PAN, expiry, tokenised credentials | **Restricted** (PCI scope) | ~94,000 cards |
| D5 | Behavioural | Device ID, IP, session, app telemetry | Internal | continuous |
| D6 | Employee | HR records, payroll, performance | Confidential | 450 |
| D7 | Credentials | Password hashes, tokens, API keys | **Restricted** | — |

Card data (D4) is the narrowest scope: FinServe does not store PANs. Card
issuing and processing is performed by Corebridge, and the mobile app displays
tokenised references only. The PCI DSS SAQ completed in 2025 was scoped on that
basis.

## 2. Principal flows

```mermaid
flowchart TB
    CUST(["Customer<br/>mobile / web"])

    subgraph AZ["Azure — sub-prod"]
        API["API gateway<br/>APIM / AKS"]
        ONB["Onboarding service"]
        PAY["Payments service"]
        STMT["Statements service"]
        SQL[("Azure SQL MI<br/>D1 D3 D5")]
        BLOB[("Storage<br/>D2 documents, statements")]
    end

    subgraph EXT["Third parties"]
        KYC["VerifyNG<br/>BVN / NIN verification"]
        CORE["Corebridge<br/>core banking + cards"]
        SMS["RouteSMS<br/>OTP and alerts"]
        PARTNER["Partner bank<br/>payment file exchange"]
    end

    subgraph ONP["On-premises — DC-LOS"]
        SFTPSRV["SFTP server<br/>payment files"]
        RECON["FinRecon<br/>reconciliation"]
    end

    EXO["Exchange Online<br/>shared mailbox"]

    CUST -->|"F1 D1 D2"| API --> ONB
    ONB -->|"F2 D2"| KYC
    ONB --> SQL
    ONB -->|"F3 D2 images"| BLOB
    CUST -->|"F4 D3"| API --> PAY
    PAY -->|"F5 D3"| CORE
    PAY -->|"F6 D1 phone"| SMS
    CORE -->|"F7 D3 nightly"| SFTPSRV
    SFTPSRV -->|"F8 D3"| PARTNER
    SFTPSRV --> RECON
    EXO -->|"F9 D3 IMAP basic auth"| RECON
    STMT --> SQL
    STMT --> BLOB
    SQL -->|"F10 D1 D3 nightly"| UAT[("sqldb-uat<br/>sub-nonprod")]
```

| Flow | Description | Data | Transport | Frequency |
|---|---|---|---|---|
| F1 | Customer submits onboarding | D1, D2 | TLS 1.2+ | On demand |
| F2 | BVN/NIN verification | D2 | HTTPS, mutual TLS, API key | Per onboarding |
| F3 | ID document upload | D2 | TLS, stored SSE | Per onboarding |
| F4 | Transfer initiation | D3 | TLS 1.2+ | ~48k/day |
| F5 | Core banking posting | D3 | IPsec S2S, REST | Real time |
| F6 | OTP / transaction alert | D1 (phone), D3 (amount) | HTTPS to SMS aggregator | ~62k/day |
| F7 | End-of-day settlement extract | D3 | Corebridge → SFTP, SSH | Nightly 23:30 |
| F8 | Partner bank file delivery | D3 | SFTP | Nightly 00:15 |
| F9 | Reconciliation confirmations | D3 | IMAP basic auth (see §4) | Nightly |
| F10 | UAT data refresh | D1, D3 | Internal, within Azure | Nightly 02:00 |

## 3. Third parties

| Party | Service | Data received | Location | Contract | DPA |
|---|---|---|---|---|---|
| Corebridge Technologies Ltd | Core banking, card processing | D1, D3, D4 | Lagos + Johannesburg DR | MSA 2021, renewed 2024 | Yes |
| VerifyNG Ltd | BVN / NIN verification | D2 | Lagos | SaaS agreement 2023 | Yes |
| RouteSMS Solutions | SMS delivery | D1 (phone), D3 (amount in message body) | Lagos, routes via Mauritius | Reseller terms | **No — standard T&Cs only** |
| Partner bank (Meridian Trust) | Settlement file exchange | D3 | Lagos | Interbank agreement 2019 | Pre-dates NDPA |
| Microsoft | Azure, M365 | All categories | `northeurope` / `westeurope` | Microsoft Product Terms + DPA | Yes |
| FinRecon (Solvex Systems) | Reconciliation desktop tool | D3 | On-premises, vendor support access | Licence 2023 | No |

Supplier due diligence was performed on Corebridge and VerifyNG at
procurement. RouteSMS was onboarded by the marketing team in 2022 for campaign
messaging and later extended to transactional OTP delivery without a
re-assessment.

## 4. The reconciliation path

The nightly settlement cycle is the oldest flow in the estate and the least
changed since the on-premises era.

Corebridge writes an end-of-day extract to the DC-LOS SFTP server at 23:30.
A scheduled task on that server transforms the file and delivers it to Meridian
Trust at 00:15. FinRecon then reads confirmation emails from a shared mailbox
and produces the reconciliation report circulated to finance by 07:00.

The delivery script authenticates to Meridian Trust with a static credential.
An extract from the scheduled task's configuration:

```ini
; deliver.cfg — DC-LOS settlement delivery
[target]
host     = sftp.meridiantrust.example
port     = 22
user     = finserve_settle
password = Settl3m3nt!Feb2019                  ; SIM-FAKE scenario-02
key_file =                                     ; unused
```

The credential has not been rotated since the arrangement began. Meridian
Trust's own security review in 2024 recommended key-based authentication;
FinServe's response, recorded in the supplier file, was that the change would
require Solvex to modify FinRecon and that it would be scheduled alongside the
DC-LOS decommission.

## 5. Cross-border transfer

The Azure tenant's primary region is `northeurope` (Ireland) with
`westeurope` (Netherlands) as paired region. Personal data in categories D1–D5
is therefore processed outside Nigeria.

The position recorded in the 2024 legal opinion is that transfer is permitted
under NDPA 2023 s.41 on the basis of adequacy, Ireland and the Netherlands
being subject to the EU GDPR, supported by the Microsoft DPA and standard
contractual clauses. The opinion notes as an open point that the NDPC's
adequacy determinations had not been published at the time of writing and
recommended review once they were.

RouteSMS message routing transits Mauritius. This was identified during the
2025 data mapping exercise and has not yet been assessed.

## 6. Retention

| Category | Retention | Basis |
|---|---|---|
| D1, D3 — account records | 7 years after closure | CBN record keeping |
| D2 — KYC documents | 7 years after closure | CBN AML/CFT |
| D4 — card | Held by Corebridge, per their schedule | Contract |
| D5 — behavioural | 7 years (falls under tenant-wide M365 policy where in scope; indefinite in SQL) | None identified |
| D6 — employee | 6 years after leaving | Employment practice |
| D7 — credentials | Life of account | — |

D5 behavioural data in Azure SQL has no deletion routine. The table
`dbo.SessionTelemetry` holds rows from the 2023 launch onward.

## 7. Data subject rights

Access, rectification and erasure requests arrive via
`dpo@finserve.ng` and are handled manually by the DPO with support from the
platform team. There is no automated discovery across systems; fulfilment
involves queries against Azure SQL, a search in Purview for M365 content, and a
ticket to Corebridge.

Mean time to fulfil an access request in 2025 was 24 days against the NDPA's
one-month expectation. Six requests were received in the year.

Erasure is complicated by the 7-year regulatory retention: the documented
position is that erasure requests from customers with a closed account inside
the retention window are refused with an explanation, and the record is
flagged rather than deleted.

## 8. Regulatory context

- **NDPA 2023** — lawful basis, data subject rights, cross-border transfer,
  breach notification to the NDPC within 72 hours, DPO appointment
- **CBN Risk-Based Cybersecurity Framework** — data classification, third-party
  risk management, incident reporting to CBN
- **PCI DSS v4.0** — SAQ-scoped; FinServe does not store PAN
- **CBN AML/CFT Regulations** — KYC record retention

## 9. Known gaps

Recorded in the data protection working file:

- RouteSMS has no DPA and no completed supplier assessment
- Meridian Trust interbank agreement pre-dates NDPA and has no processor clauses
- Retention schedule drafted 2024, unsigned
- No deletion routine for D5 behavioural data
- NDPC adequacy determinations not re-checked since the 2024 legal opinion
- Mauritius routing in the SMS path unassessed
- DSAR fulfilment manual, mean 24 days against a 30-day obligation
