# 02-ARCHITECTURE

Technical architecture of **FinServe Digital Bank Ltd**, the fictional client
in Project Sentinel. This is the estate the GRC team risk-assesses and the SOC
team defends.

> **Fictional.** FinServe does not exist. Every host, address, account name and
> vendor here is invented for training. Any resemblance to a real institution
> is coincidental. Nothing in this directory describes real infrastructure
> belonging to Sycom or any client.

## Documents

| # | Document | Primary audience |
|---|---|---|
| 01 | [Network Diagram](01-Network-Diagram.md) — zones, segmentation, egress, remote access | SOC, then GRC |
| 02 | [Azure Architecture](02-Azure-Architecture.md) — subscriptions, hub-spoke, workloads, data services | Both |
| 03 | [M365 Architecture](03-M365-Architecture.md) — tenant, identity, collaboration, endpoint | Both |
| 04 | [Data Flow](04-Data-Flow.md) — what data moves where, classification, third parties | GRC, then SOC |

Read 02 before 01 if you are new to Azure; the network document assumes the
subscription layout.

## How to use this material

**GRC track.** These four documents are your source material for the asset
register, the risk register and the supplier register. Everything you need to
populate them is here — systems, owners, data classifications, third parties,
hosting locations. Where a document does not say something, that absence may
itself be worth recording. Do not invent facts to fill a gap; raise it as a
question or record it as an assumption and say so.

**SOC track.** Sections headed *Logging and telemetry* in each document tell
you what is collected, from where, and for how long. Build your view of the
detection surface from those. When an inject lands, your first question is
usually "would we have seen this, and in which log source" — these documents
are where that gets answered.

## This is a real estate, not a clean one

FinServe is a mid-size bank that has grown by acquisition and migrated to cloud
in stages. The architecture reflects that: there is legacy alongside modern,
there are exceptions granted under commercial pressure, and there are decisions
that were reasonable when made and have not been revisited.

The documents describe the estate **as it is**, in the voice of the people who
built it — which means they are not neutral. Internal architecture
documentation tends to understate the things its authors are least comfortable
about. Treat confident phrasing as a claim to be tested, not a fact. Several
statements here are things FinServe *believes* about itself.

Finding what is wrong is the exercise. Nothing in this directory is labelled as
a weakness, and that is deliberate.

## Scope and assumptions

| Assumption | Value | Change if wrong |
|---|---|---|
| Regulator | PRA-authorised, dual-regulated by PRA and FCA | Swap the *Regulatory context* section in each document |
| Data protection regime | UK GDPR + DPA 2018, ICO as supervisory authority | Same |
| AML regime | Money Laundering Regulations 2017 | Retention tables in 03 and 04 |
| Financial year | January–December | 00-ADMIN schedule |
| Estate size | ~450 staff, ~180,000 retail customers | Asset register scale |

The regulatory framing is confined to one clearly marked section per document
so it can be swapped for a different jurisdiction without rewriting the
technical content.

## Changes

Architecture is mentor-owned scenario material. Interns raise questions as
issues or in PR review; they do not edit this directory. If an inject changes
the estate mid-simulation, the change lands here as a `mentor/` branch PR so
the estate has a version history the board session can refer back to.
