# FinServe — Asset Register

**Owner:** Head of Infrastructure · **Maintained by:** Infrastructure team
**Last full review:** March 2024 · **Updated since:** by exception

---

| # | Asset | Owner | Environment | Criticality |
|---|---|---|---|---|
| A-001 | Azure Production | Cloud Platform Lead | Cloud | High |
| A-002 | Azure Non-Production | Cloud Platform Lead | Cloud | Medium |
| A-003 | Microsoft 365 | Head of Digital Workplace | Cloud | High |
| A-004 | Corebridge core banking | CTO | SaaS | High |
| A-005 | DC-SLO — rack 1, compute | Head of Infrastructure | On-premises | Medium |
| A-006 | DC-SLO — rack 2, storage | Head of Infrastructure | On-premises | Medium |
| A-007 | DC-SLO — SFTP server | Head of Infrastructure | On-premises | Low |
| A-008 | DC-SLO — backup appliance | Head of Infrastructure | On-premises | Medium |
| A-009 | FinRecon reconciliation tool | Head of Finance Operations | On-premises | Medium |
| A-010 | Active Directory — finserve.local | Head of Infrastructure | Hybrid | High |
| A-011 | Entra Connect server | Head of Infrastructure | Hybrid | High |
| A-012 | JUMP-01 administrative host | Head of Infrastructure | Cloud | Medium |
| A-013 | Fortigate firewall pair — HQ | Head of Infrastructure | On-premises | High |
| A-014 | Fortigate firewall pair — DC-SLO | Head of Infrastructure | On-premises | Medium |
| A-015 | Branch firewall — Manchester | Head of Infrastructure | On-premises | Low |
| A-016 | Branch firewall — Birmingham | Head of Infrastructure | On-premises | Low |
| A-017 | Branch firewall — Leeds | Head of Infrastructure | On-premises | Low |
| A-018 | HQ network — switching and wireless | Head of Infrastructure | On-premises | Medium |
| A-019 | ExpressRoute circuits | Head of Infrastructure | Network | High |
| A-020 | Site-to-site VPN — branches | Head of Infrastructure | Network | Medium |
| A-021 | Mobile application — iOS | Head of Product | Cloud | High |
| A-022 | Mobile application — Android | Head of Product | Cloud | High |
| A-023 | Internet banking web front end | Head of Product | Cloud | High |
| A-024 | Public website and marketing pages | Head of Marketing | Cloud | Low |
| A-025 | Azure DevOps — repositories and pipelines | CTO | SaaS | Medium |
| A-026 | Microsoft Sentinel | CISO | Cloud | Medium |
| A-027 | Defender for Endpoint | CISO | Cloud | Medium |
| A-028 | Intune — endpoint management | Head of Digital Workplace | Cloud | Medium |
| A-029 | Corporate laptops — Windows | Head of Digital Workplace | Endpoint | Medium |
| A-030 | Corporate laptops — macOS | Head of Digital Workplace | Endpoint | Low |
| A-031 | Corporate mobile devices | Head of Digital Workplace | Endpoint | Low |
| A-032 | Contact centre desktops | COO | Endpoint | Medium |
| A-033 | Contact centre telephony platform | COO | SaaS | High |
| A-034 | HR system | Chief People Officer | SaaS | Medium |
| A-035 | Payroll | Chief People Officer | SaaS | Medium |
| A-036 | Finance general ledger | CFO | SaaS | High |
| A-037 | Procurement and contract management | CFO | SaaS | Low |
| A-038 | Complaints tracking (spreadsheet-based) | COO | On-premises | Low |
| A-039 | Board portal | Company Secretary | SaaS | Medium |
| A-040 | Branch counter systems | COO | On-premises | Low |
| A-041 | Card management — via Corebridge | COO | SaaS | High |

**41 entries.**

---

## Maintenance notes

Entered by the infrastructure team at the March 2024 review. Since then,
entries have been added or amended when someone has raised a change that
prompted it. There is no periodic reconciliation against the estate and no
joiner/mover/leaver trigger.

Criticality is assigned by the asset owner on a High / Medium / Low scale.
There is no documented definition of the three levels.

The register was built to support the 2023 audit, which asked whether the bank
knew what it had. It has not been re-scoped since.

## Fields not held

Recorded here for completeness, as raised by Internal Audit in the 2024
handover:

- Data classification or category
- Personal data — yes/no, and of what kind
- Hosting location or jurisdiction
- Supporting supplier, where applicable
- Link to the business process or service the asset supports
- Recovery objectives
- Lifecycle status — supported, extended support, end of life
