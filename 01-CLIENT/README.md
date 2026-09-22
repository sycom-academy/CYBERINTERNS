# 01-CLIENT

**FinServe Digital Bank Ltd** — the fictional client in Project Sentinel.

> **Fictional.** FinServe does not exist. Every person, figure, vendor and
> address here is invented for training. Any resemblance to a real institution
> or individual is coincidental.

## Documents

| # | Document | What it gives you |
|---|---|---|
| 01 | [Company Profile](01-Company-Profile.md) | What the bank is, how it got here, what it is worth, how it is regulated |
| 02 | [Organisation Chart](02-Organisation-Chart.md) | Who reports to whom, board and committees, headcount, vacancies |
| 03 | [Business Processes](03-Business-Processes.md) | What the bank actually does, end to end, and what each process depends on |
| 04 | [Stakeholders](04-Stakeholders.md) | Who you will deal with, what they want, and what they are under pressure about |

## How to use this

**GRC track.** This is where business context comes from. The architecture
tells you what systems exist; this tells you what they are *for*, who owns
them, and what it costs the bank when they stop. You cannot score a risk
without that, and you cannot identify an important business service under the
operational resilience rules from a network diagram alone.

Document 03 is the one to read twice. Impact tolerances attach to business
services, not to systems.

**SOC track.** Read 02 and 04 properly even though they look like GRC material.
Knowing who holds what access, which teams are short-staffed, and who talks to
whom is how you tell a plausible action from an implausible one during an
investigation. Document 04 in particular tells you who to go to for what.

## A note on how this is written

These documents are FinServe's own. They are written the way a bank writes
about itself for an incoming adviser: accurate on the facts, selective about
emphasis, and more confident in places than the evidence warrants.

Where a document states something as settled, that is FinServe's position, not
a finding you can adopt. Check it against `02-ARCHITECTURE/` before you rely on
it. Where the two disagree, the disagreement is the interesting part.
