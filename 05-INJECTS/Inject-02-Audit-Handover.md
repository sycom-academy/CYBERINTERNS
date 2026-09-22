# Inject 02 — Internal audit handover

**Release:** Week 1, Day 2, 09:00 · **Team:** GRC · **Deliverable due:** W1 D5

---

## The artefact

> **From:** Daniel Whitcombe, Head of Internal Audit
> **To:** Project Sentinel — GRC workstream
> **Date:** W1 D2
> **Subject:** FW: Registers — as requested. Please read the caveat.
>
> Priya asked me to send you what we hold. Attached below in summary form.
>
> The caveat: I would not rely on any of it. The asset register was built for
> the 2023 audit and has been updated by exception since, which in practice
> means when somebody remembered. The risk register is maintained by the
> second line and reviewed quarterly, but the reviews have become a discussion
> about whether scores should move rather than whether the risks are still the
> right risks. The supplier register was built by procurement for contract
> renewal dates and was never designed to answer a data protection question.
>
> I am telling you this because I would rather you rebuilt them from the
> architecture than inherited our blind spots.
>
> **Asset register — summary**
> 41 entries. Fields: name, owner, environment, criticality. No data
> classification field. Last full review March 2024. Cloud resources are
> represented as three entries: "Azure Production", "Azure Non-Production",
> "Microsoft 365".
>
> **Risk register — summary**
> 18 open risks. Highest scored:
>
> | ID | Risk | Score | Owner | Last moved |
> |---|---|---|---|---|
> | R-04 | Core banking outage causes customer detriment | 20 | CTO | 2024-06 |
> | R-09 | Ransomware affecting corporate estate | 16 | CISO | 2024-02 |
> | R-11 | Key person dependency, platform team | 16 | CTO | 2025-01 |
> | R-02 | Regulatory censure following cyber incident | 15 | CISO | 2024-02 |
> | R-17 | Failure to meet operational resilience impact tolerances | 12 | COO | 2025-03 |
>
> There is no entry relating to third-party data processing, to
> non-production environments, or to privileged access.
>
> **Supplier register — summary**
> 63 suppliers. Fields: name, contract owner, annual value, renewal date,
> criticality (high/medium/low). No field for what data they receive, where
> they process it, or whether a DPA exists. Corebridge, Microsoft and
> Meridian Trust are marked high. IDVerify is medium. Textway is low.
> Solvex Systems does not appear.
>
> One more thing, since you will find it anyway. The 2024 audit raised eleven
> findings. Nine are closed. The two open ones are:
>
> - **IA-2024-07** — *Privileged access is standing rather than
>   just-in-time.* Management response: PIM rollout, target Q3 2025. Revised
>   to Q2 2026 in January.
> - **IA-2024-11** — *Data retention schedule not formally approved.*
>   Management response: schedule to be signed off by the Data Protection
>   Officer, target Q1 2025. No revised date recorded.
>
> Daniel Whitcombe
> Head of Internal Audit

---

## What you are asked to produce

**GRC team.**

Rebuild the three registers from the architecture. Not a tidy-up of what audit
sent — a rebuild, from `02-ARCHITECTURE/` and `01-CLIENT/`.

**1. Asset register** → `06-DELIVERABLES/GRC/Asset-Register.md`

At minimum, per asset: identifier, description, owner, environment, the data
categories it holds (use D1–D7 from `04-Data-Flow.md`), business criticality,
and whether it is in scope for an important business service under operational
resilience. Decide your own granularity and say why — "Azure Production" as one
line is clearly wrong, one line per resource is clearly unusable.

**2. Risk register** → `06-DELIVERABLES/GRC/Risk-Register.md`

Per risk: identifier, description in cause-event-consequence form, the assets
and data affected, inherent score, the controls you can evidence from the
architecture, residual score, owner, and your recommended treatment. State your
scoring scale; do not borrow FinServe's without saying so.

Write the risks you find. If a risk audit has open at a score of 16 does not
survive contact with the architecture, say that too — a register that only
grows is not a register, it is a list.

**3. Supplier register** → `06-DELIVERABLES/GRC/Supplier-Register.md`

Per supplier: name, service, data categories received, processing location,
whether the transfer leaves the UK and on what basis, contract and DPA status,
whether it constitutes material outsourcing under PRA SS2/21, and your
assessment of the risk.

## Where it goes

`06-DELIVERABLES/GRC/`, one PR per register or one PR for all three — your
choice, but say which you are doing in the PR description.

## Time budget

Three days. This is the largest single piece of GRC work in the pilot and
everything in week three depends on it.

## Note

You have been handed three registers and told not to trust them. That is a
gift, not an obstacle. The gap between what the registers say and what the
architecture shows is itself a finding, and the board will care about it more
than they care about your scoring methodology.
