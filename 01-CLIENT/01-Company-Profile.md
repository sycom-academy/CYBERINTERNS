# FinServe Digital Bank Ltd — Company Profile

**Prepared for:** Project Sentinel · **Prepared by:** Office of the CEO
**Date:** W1 D1

---

## 1. At a glance

| | |
|---|---|
| Legal entity | FinServe Digital Bank Ltd |
| Incorporated | England and Wales, 2018 |
| Registered office | 14 Cabot Square, Canary Wharf, London E14 |
| Authorisation | PRA-authorised, dual-regulated by the PRA and the FCA |
| Deposit protection | FSCS, £85,000 per eligible depositor |
| Ownership | Privately held. Four institutional investors, founder stake ~11% |
| Staff | 450 (FTE 431) |
| Retail customers | ~180,000 |
| Accounts | ~215,000 current and savings |
| Cards issued | ~94,000 debit |
| Customer deposits | £1.41bn |
| Lending book | £684m — personal loans, arranged overdrafts |
| Revenue, FY2025 | £94.2m |
| Profit before tax, FY2025 | £3.2m — first full-year profit |

## 2. What the bank does

FinServe is a mobile-first retail bank. Current accounts, instant-access and
fixed-term savings, unsecured personal lending, and arranged overdrafts. No
mortgages, no business banking, no investment products.

Customers open accounts in the app in under ten minutes, which is the
proposition the bank was built on and the one it markets. Roughly 94% of
customer interactions are in-app. The remainder are the contact centre and,
for a shrinking minority, the three branches.

The branches are a legacy of the Kestrel acquisition (§3) and their future is
under review. They serve about 4,100 customers regularly, skewing older, and
the board has so far declined to close them on reputational grounds.

## 3. How it got here

**2018 — Authorisation.** Founded by Gavin Marsh and two others, authorised
with restriction, mobilisation completed 2019.

**2019–2021 — Growth.** Current accounts and savings. Reached 60,000 customers
by end-2021. Core banking on an early platform that did not scale.

**2022 — The Kestrel acquisition.** FinServe acquired Kestrel Savings Ltd, a
Slough-based savings institution founded in 1974, for £41m. Kestrel brought
£390m of deposits, around 38,000 customers, three branches, 94 staff and a
co-located data centre in Slough.

The commercial logic was deposits and a banking licence footprint. The
integration plan was eighteen months. Four years on, the Slough data centre is
still running eleven workloads, some Kestrel-era processes have never been
re-engineered, and the settlement arrangement with Meridian Trust — inherited
from Kestrel, dating to 2019 — is still in place.

**2023–2024 — Project Lighthouse.** Migration to Azure and Microsoft 365, and
replacement of the core banking platform with Corebridge. Delivered broadly on
time. The programme's stated scope was infrastructure and core banking; control
uplift was descoped in early 2024 to protect the delivery date and was not
separately funded afterwards.

**2025 — Profitability.** First full-year profit. Headcount grew from 366 to
450 during the year, concentrated in engineering and the contact centre.

**Now.** A Series D raise of £75m is in progress, expected to close in
approximately six weeks. Proceeds are earmarked for lending growth and a
mortgage proposition in 2027.

## 4. Regulatory position

Dual-regulated. The PRA supervises prudential soundness; the FCA supervises
conduct. Both matter here.

| Framework | Relevance |
|---|---|
| PRA SS1/21, FCA PS21/3 — Operational resilience | Important business services identified and mapped, impact tolerances set and tested. See [03-Business-Processes.md](03-Business-Processes.md) §5 |
| PRA SS2/21 — Outsourcing and third party risk | Corebridge and Microsoft are material outsourcing arrangements. Register maintained by procurement |
| FCA SYSC | Systems and controls, including the control functions in [02-Organisation-Chart.md](02-Organisation-Chart.md) |
| UK GDPR / DPA 2018 | ICO-supervised. DPO appointed |
| Money Laundering Regulations 2017 | MLRO appointed. Customer due diligence at onboarding |
| Payment Services Regulations 2017 | Strong Customer Authentication on payment initiation |
| Consumer Duty | Applies across the retail proposition |

**Supervisory history.** No enforcement action. Two matters on the record:

- **2023** — PRA letter following the Kestrel integration, noting the pace of
  change relative to the control environment and asking for a board-approved
  integration assurance plan. A plan was submitted and the matter closed in
  2024.
- **2025** — FCA information request relating to app availability after three
  outages in Q1. Responded to; no further action. Internally attributed to the
  Corebridge cutover.

**Operational resilience self-assessment** was last approved by the board in
March 2025. It identifies five important business services and sets impact
tolerances for each. It has not been revised since.

## 5. Technology posture

The estate is described in `02-ARCHITECTURE/`. Two points of context the
architecture does not give:

**Speed has been the organising principle.** FinServe competes on shipping
faster than incumbents, and the engineering culture reflects that. Change
volume is high — around 140 production changes a month. The change advisory
board meets weekly and approves the majority by exception.

**Security spend has been reactive.** The security function was established in
2022 after the Kestrel acquisition raised it at diligence. Sentinel was bought
in 2024 as part of Lighthouse. There is no multi-year security roadmap with
funding attached; investment has been approved incident by incident and
finding by finding.

The FY2026 technology budget is £14.1m, of which security is £610k including
salaries.

## 6. What the board is worried about

From the minutes of the March 2025 and September 2025 board meetings:

1. **Funding round execution.** Dominant, and the lens through which most other
   items are currently viewed.
2. **Core banking stability.** Three Q1 outages. Improved since.
3. **Cost-to-income ratio** at 78%, against a target of 65% by 2027.
4. **Slough.** The cost of running it and the cost of closing it.
5. **Regulatory change capacity** — Consumer Duty and operational resilience
   work competing with the growth agenda for the same people.

Cyber risk appears in the risk report each quarter and has not been the subject
of substantive board discussion since the 2023 PRA letter.

## 7. Why Project Sentinel exists

The board asked for independent assurance in December, prompted by a
combination of the funding round diligence process and the CISO's own view that
the control environment has not kept pace with the architecture.

There is no known incident driving it. The CISO's engagement letter to the
review team states this directly.
