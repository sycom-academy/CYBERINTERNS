# 04-SOC

**FinServe's existing security operations material.** What the SOC function
holds today, handed over by the Security Operations Manager in
[Inject 03](../05-INJECTS/Inject-03-SIEM-Health-Review.md).

> **Source material, not good practice.** Marcus Ifill told you the Sentinel
> deployment was signed off as complete and is not, and that he is not
> confident what two of the custom rules do. Both statements are accurate and
> both are evidenced here.

## Contents

| Path | Document |
|---|---|
| `Logs/` | [Log source inventory](Logs/Log-Source-Inventory.md) — what is collected, from where, for how long |
| `Alerts/` | [Analytics rules](Alerts/Analytics-Rules.md) — enabled rules, including the four custom ones, with their KQL |
| `Alerts/` | [Alert summary, last 30 days](Alerts/Alert-Summary-30-Days.md) — 847 alerts and what happened to them |
| `IOCs/` | [IOC register](IOCs/IOC-Register.md) |
| `Threat-Intel/` | [Threat profile 2025](Threat-Intel/Threat-Profile-2025.md) |
| `Incident-Tickets/` | [Incident log](Incident-Tickets/Incident-Log-2025.md) — recorded incidents to date |

## What you do with it

Your deliverables go in `06-DELIVERABLES/SOC/`, not here. This directory is the
state of the function as you found it and does not change during the
engagement.

The log source inventory is the primary input to the detection surface map
Inject 03 asks for. **Do not simply reformat it.** It records what the
infrastructure team believes is collected. Check it against the *Logging and
telemetry* sections of each architecture document, and where they disagree,
that disagreement is the finding.

The analytics rules document contains the actual KQL. Read it as an analyst
would read a colleague's code: what does each rule fire on, what would it miss,
and — for each one — is the data it queries actually being ingested?

## The team

Three people. Marcus Ifill (Security Operations Manager) and Joel Amankwah
(Security Analyst, joined September 2025) cover monitoring between them. The
CISO does not work the queue. There is no out-of-hours rota; alerts outside
working hours page Marcus Ifill's mobile.

## Conventions

Timestamps are UTC. In-world dates are relative where they relate to the
scenario timeline (`W2 D1`) and absolute where they are historical.
