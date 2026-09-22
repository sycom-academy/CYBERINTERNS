# 05-INJECTS

Scripted injects for the four-week pilot. Mentor-owned. Released on schedule;
interns do not read ahead.

> **Inject cards carry the stimulus and the ask. They do not carry the
> answers.** Expected findings, model responses and per-inject marking guidance
> are tier C material and live in the private assessment repository, not here.
> See [`00-ADMIN/PROGRAMME-ARCHITECTURE.md`](../00-ADMIN/PROGRAMME-ARCHITECTURE.md) §1.

## The arc

One incident, discovered late, in a bank that has been carrying the conditions
for it for two years. Weeks 1–2 look like routine work. They are not — the
material the teams gather in week 1 is what they need in week 3, and a team
that treats the baseline as busywork will feel it.

| Week | Shape | GRC | SOC |
|---|---|---|---|
| 1 | Baseline | Asset, risk and supplier registers from the architecture | Detection surface, log coverage, SIEM health |
| 2 | First signals | A supplier's breach notification | A phishing campaign that partly succeeds |
| 3 | Escalation | Personal data breach assessment, regulatory clock | Lateral movement, timeline, containment |
| 4 | Account | Board pack, remediation plan, reporting decisions | Board pack, incident narrative, detection gaps |

The week-3 convergence is deliberate: both teams arrive at the same fact from
opposite directions, and neither can answer the board alone.

## Schedule

| # | Inject | Week / day | Team | Deliverable due |
|---|---|---|---|---|
| 01 | [Engagement letter](Inject-01-Engagement-Letter.md) | W1 D1 09:00 | Both | W1 D2 |
| 02 | [Internal audit handover](Inject-02-Audit-Handover.md) | W1 D2 09:00 | GRC | W1 D5 |
| 03 | [SIEM health review](Inject-03-SIEM-Health-Review.md) | W1 D2 09:00 | SOC | W1 D5 |
| 04 | [Invoice phish](Inject-04-Invoice-Phish.md) | W2 D1 08:40 | SOC | W2 D3 |
| 05 | [Supplier breach notification](Inject-05-Supplier-Breach.md) | W2 D3 14:00 | GRC | W2 D5 |
| 06 | [Anomalous mailbox access](Inject-06-Mailbox-Access.md) | W3 D1 07:15 | SOC | W3 D3 |
| 07 | [Non-production data discovery](Inject-07-UAT-Data-Discovery.md) | W3 D2 11:00 | Both | W3 D4 |
| 08 | [The regulatory clock](Inject-08-Regulatory-Clock.md) | W3 D3 16:30 | GRC | W3 D5 |
| 09 | [Board pack brief](Inject-09-Board-Pack-Brief.md) | W4 D1 09:00 | Both | W4 D3 09:00 |
| 10 | [Board curveball](Inject-10-Board-Curveball.md) | W4 D4, in session | Both | Live |

Times are in-world. Release them at the equivalent point in the working day if
you can — an inject that lands at 07:15 reads differently from one handed over
at a scheduled session, and part of what is being assessed is how a team
behaves when something arrives before they are ready.

## Card format

Each card has the same five parts:

1. **Release** — week, day, time, target team
2. **The artefact** — what arrives, in world: an email, a ticket, an alert, a
   letter. Written as the thing itself, not as a description of it
3. **What you are asked to produce** — the deliverable, explicitly
4. **Where it goes** — path in `06-DELIVERABLES/`
5. **Time budget** — indicative, not a limit

## Conventions

- Deliberately fake credentials carry `SIM-FAKE` so the secret scanner lets
  them through. Mentors only — see `.gitleaks.toml`.
- In-world dates are relative (`W2 D1`). Substitute real dates when you run it.
- All artefacts are fictional, including sender names, domains and addresses.
  Domains use `.example` or the fictional `finserve.example` estate.
- New injects: `Inject-NN-Short-Name.md`, add a row to the schedule above.

## Running notes

Injects 04, 06 and 07 form a single chain. If the SOC team stalls on 04, 06
still releases on time — the incident does not wait for the responders, and
a team that missed the first signal discovering it retrospectively at 06 is a
legitimate and instructive outcome, not a failure of the exercise.

Inject 07 is the hinge. Both teams receive it simultaneously and neither has
the whole picture. Resist the urge to help them find each other.
