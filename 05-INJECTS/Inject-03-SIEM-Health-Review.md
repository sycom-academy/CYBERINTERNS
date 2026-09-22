# Inject 03 — SIEM health review

**Release:** Week 1, Day 2, 09:00 · **Team:** SOC · **Deliverable due:** W1 D5

---

## The artefact

> **From:** Marcus Ifill, Security Operations Manager
> **To:** Project Sentinel — SOC workstream
> **Date:** W1 D2
> **Subject:** Sentinel — what you're inheriting
>
> Morning. Priya said you'd want a picture of where the SIEM actually is, so
> here it is without the marketing.
>
> We deployed Sentinel in 2024 as part of Lighthouse. The deployment was done
> by the partner who did the Azure migration, and it was signed off as
> complete. It is complete in the sense that it exists and connectors are on.
> It is not complete in the sense of "we would catch things".
>
> **Connectors on:** Azure Activity, Entra ID sign-in and audit, Microsoft 365,
> Defender for Cloud, Azure Firewall, Azure WAF, Microsoft threat intelligence.
>
> **Connectors off or never done:** Azure SQL audit, Storage diagnostics, AKS
> audit log. The SQL one bothers me most and I have raised it twice.
>
> **Analytics rules:** the Microsoft built-in templates for Entra ID, Azure
> Activity and Azure Firewall, enabled as shipped. Plus four custom KQL rules
> the partner wrote during deployment. I did not write them and I am not
> confident what two of them do.
>
> **Alert volume, last 30 days:** 847 alerts. 812 closed as benign positive or
> false positive. 31 closed as "informational". 4 investigated properly. Our
> median time to first touch is about six hours, which sounds bad until you
> consider the volume and that there are two of us.
>
> **Retention:** 60 days in the workspace. I asked for a year in the 2025
> budget round and did not get it.
>
> **What I would want to know if I were you.** We have systems that generate
> no telemetry we can see. I know the branch firewalls are one. I suspect
> there are others. Nobody has ever sat down and drawn a line between "things
> that exist" and "things we would see something on", and that is the exercise
> I would do first.
>
> Ask me for KQL, access, whatever. I am in the office most days.
>
> Marcus

---

## Reference data

The **Logging and telemetry** sections of each architecture document are your
primary source:

- [`02-ARCHITECTURE/01-Network-Diagram.md`](../02-ARCHITECTURE/01-Network-Diagram.md) §6
- [`02-ARCHITECTURE/02-Azure-Architecture.md`](../02-ARCHITECTURE/02-Azure-Architecture.md) §7
- [`02-ARCHITECTURE/03-M365-Architecture.md`](../02-ARCHITECTURE/03-M365-Architecture.md) §7

---

## What you are asked to produce

**SOC team.**

**1. Detection surface map** → `06-DELIVERABLES/SOC/Detection-Surface.md`

For every system in the estate, state: does it produce security-relevant
telemetry, does that telemetry reach Sentinel, how long is it kept, and is
there an analytics rule that would fire on it. Four columns, one honest answer
per system. Where the answer is no, say what that means in practice — not
"no coverage" but "an attacker doing X here would be invisible".

Organise it so that someone can look at a system and immediately see whether
it is watched. The registers the GRC team are building cover what exists; yours
covers what is seen. They should be readable side by side.

**2. Coverage gap assessment** → `06-DELIVERABLES/SOC/Coverage-Gaps.md`

The gaps, ranked. For each: the system, what an attacker could do unobserved,
what it would take to close it, and how hard that is. Rank by what the gap
would cost, not by how easy it is to fix.

Pay attention to the retention figure. A gap in coverage and a gap in retention
are not the same problem and the board will conflate them if you let them.

**3. Detection recommendations** → `06-DELIVERABLES/SOC/Detection-Backlog.md`

Five to ten detections you would build, in priority order. For each: what it
detects, which log source it needs, roughly what the logic is, and what would
make it noisy. You may write KQL. You will not be marked down for KQL that does
not run, and you will be marked down for a detection whose data source is not
actually collected.

## Where it goes

`06-DELIVERABLES/SOC/`. One PR is fine.

## Time budget

Three days. Everything you do in weeks two and three is easier if this is
honest and harder if it is optimistic.

## Note

Marcus has told you the deployment was signed off as complete and is not. He
has also told you two of the four custom rules are a mystery to him. Both
statements are evidence. The board signed a cheque for a SIEM in 2024 and
believes it bought detection; part of what you are establishing is the distance
between that belief and the estate.
