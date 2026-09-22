# FinServe — Indicator of Compromise Register

**Owner:** Security Operations · **As at:** W1 D1

---

## 1. What this is

A spreadsheet, exported here. It holds indicators that Security Operations has
recorded from past incidents and from ad-hoc intelligence. It is not a threat
intelligence platform and it is not connected to anything.

Indicators in this register are **not** automatically applied to Sentinel. The
`ThreatIntelligenceIndicator` table is populated by the Microsoft feed only.
There is no custom indicator ingestion, no TAXII connector, and no watchlist.
Applying anything here to a detection is a manual act that has been performed
three times.

## 2. Indicators

| # | Indicator | Type | Source | Added | Applied to a detection? |
|---|---|---|---|---|---|
| I-001 | `mail-secure-verify.example` | Domain | Phishing wave, Mar 2024 | 2024-03 | Yes — blocked at EOP |
| I-002 | `account-review-finserve.example` | Domain | Phishing wave, Mar 2024 | 2024-03 | Yes — blocked at EOP |
| I-003 | `198.51.100.42` | IPv4 | Phishing wave, Mar 2024 | 2024-03 | No |
| I-004 | `secure-docs-share.example` | Domain | Reported email, Aug 2024 | 2024-08 | No |
| I-005 | `d41d8cd98f00b204e9800998ecf8427e` | MD5 | Defender detection, Sep 2024 | 2024-09 | Defender handled |
| I-006 | `203.0.113.19` | IPv4 | Failed RDP attempts, Nov 2024 | 2024-11 | Yes — firewall deny |
| I-007 | `hr-payslip-portal.example` | Domain | Reported email, Feb 2025 | 2025-02 | No |
| I-008 | `185.199.108.153` | IPv4 | Ad-hoc intel, Apr 2025 | 2025-04 | No — source not recorded |
| I-009 | `invoice-update-secure.example` | Domain | Reported email, Jun 2025 | 2025-06 | No |

**9 indicators.** Three applied to a detection or block.

## 3. Process

There is no documented process for adding, reviewing, ageing out or retiring an
indicator. Nothing in this register has been removed since it was created.
Indicator I-008 has no recorded provenance; the analyst who added it has left.

No indicator has been enriched — there is no record of what any of these
resolve to now, whether they are still active, or whether they were ever seen
in FinServe telemetry beyond the incident that produced them.

## 4. Retrospective search

When an indicator is added, Security Operations does not routinely search
historical telemetry for it. Where this has been done it has been at the point
of the originating incident only, and the 60-day workspace retention means an
indicator added today cannot be searched further back than 60 days in any case.

## 5. Sharing

FinServe is not a member of any sector information sharing body. It does not
receive or contribute indicators to a sharing scheme. Intelligence arrives via
the Microsoft feed, vendor bulletins, and whatever the Security Operations
Manager reads.
