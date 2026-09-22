# IT Audit 2024 — Findings and Management Responses

**Audit:** Technology and information security controls
**Performed by:** Hallam Dunn LLP (co-source) with Internal Audit
**Fieldwork:** February–April 2024 · **Report issued:** May 2024
**Opinion:** Partial assurance — improvement required
**Tracked to:** September 2025

---

## Summary

Eleven findings. Nine closed, two open.

| Rating | Raised | Closed | Open |
|---|---|---|---|
| High | 3 | 2 | 1 |
| Medium | 5 | 4 | 1 |
| Low | 3 | 3 | 0 |

---

## Open findings

### IA-2024-07 — Privileged access is standing rather than just-in-time

**Rating:** High · **Status:** Open · **Raised:** May 2024

Privileged roles in Entra ID and Azure are assigned permanently. Privileged
Identity Management is licensed under the existing Entra ID P2 entitlement but
has not been configured. Fourteen individuals hold Owner on a subscription.
There is no periodic recertification of privileged role membership and no
policy or standard governing privileged access.

**Management response (May 2024).** Accepted. "PIM will be configured for all
privileged roles as part of the identity workstream. A privileged access
standard will be issued alongside." Owner: CTO. Target: Q3 2025.

**Revision (January 2025).** Target revised to Q2 2026. "Resource has been
redirected to the Corebridge migration, which the Executive Committee has
agreed takes priority."

**Internal Audit comment (September 2025).** "This finding has now been open
for sixteen months and has been deferred once. The condition it describes is
unchanged. We have raised with the Audit Committee that a second deferral
should not be agreed without a compensating control being put in place in the
interim. No compensating control has been proposed."

---

### IA-2024-11 — Data retention schedule not formally approved

**Rating:** Medium · **Status:** Open · **Raised:** May 2024

The Bank operates a tenant-wide seven-year retention rule in Microsoft 365
applied uniformly to Exchange, SharePoint, OneDrive and Teams content. There
is no approved retention schedule mapping data category to retention period
and no disposition review. The rule was configured by the Digital Workplace
team and has not been reviewed by the Data Protection Officer.

**Management response (May 2024).** Accepted. "A data retention schedule will
be drafted by the Data Protection Officer and submitted for approval." Owner:
General Counsel / DPO. Target: Q1 2025.

**Status (September 2025).** A schedule was drafted in 2024 and carries version
0.9. It has not been submitted for approval. No revised target date has been
recorded.

---

## Closed findings

| ID | Finding | Rating | Closed | Basis for closure |
|---|---|---|---|---|
| IA-2024-01 | Multi-factor authentication not enforced for all users | High | 2024-09 | Conditional Access policy 1 deployed tenant-wide |
| IA-2024-02 | Legacy authentication protocols permitted | High | 2024-11 | Conditional Access policy 3 deployed. **Closed with a documented exclusion group; see note below** |
| IA-2024-03 | No security information and event management capability | Medium | 2024-08 | Microsoft Sentinel deployed as part of Project Lighthouse |
| IA-2024-04 | Endpoint detection and response not deployed to all corporate devices | Medium | 2024-07 | Defender for Endpoint onboarded via Intune |
| IA-2024-05 | Backups not encrypted at rest in the legacy estate | Medium | 2024-06 | Backup appliance reconfigured |
| IA-2024-06 | No annual penetration test | Medium | 2024-10 | Redcastle Security engaged; test performed October 2024 |
| IA-2024-08 | Starters and leavers process not consistently followed | Low | 2024-09 | Process updated; sample retested |
| IA-2024-09 | Security awareness training completion below target | Low | 2024-08 | Completion reached 94% |
| IA-2024-10 | Asset register incomplete | Low | 2024-05 | Register refreshed at the March 2024 review |

### Note on IA-2024-02

The finding was closed on deployment of the Conditional Access policy blocking
legacy authentication. The policy carries an exclusion group,
`CA-Exclusions-Service`, which at the time of closure contained two break-glass
accounts and three service accounts.

The exclusion granted for the FinRecon reconciliation tool under change
CHG-2023-0447 pre-dates the audit. It was not separately identified in the
audit working papers and the closure testing sampled enforcement for standard
user accounts only.

### Note on IA-2024-10

The asset register was refreshed in March 2024 and the finding closed on that
basis. The scope of the finding was completeness of the register against the
estate. It did not address the fields the register holds.

---

## Audit coverage

The 2024 audit scope was agreed with the Audit Committee in January 2024. It
covered identity and access, endpoint, network, logging and monitoring, backup,
and the starters and leavers process.

The following were **out of scope** and have not been audited since:

- Non-production environments and test data
- Third-party and supplier data processing
- Cloud configuration and policy enforcement
- Data protection compliance, other than the retention finding above
- The Slough estate, other than backup encryption

The 2025 audit plan approved by the Audit Committee allocated technology
coverage to a review of the Corebridge migration, which was deferred to 2026 at
the July 2025 meeting. **There has been no technology internal audit in 2025.**
