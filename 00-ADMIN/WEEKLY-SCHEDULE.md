# Weekly Schedule

Owner: CISO. Four weeks, Scenario 1.

Cohort size and mentor allocation: [`COHORT.md`](COHORT.md). Adding or removing
people: [`JOINING.md`](JOINING.md).

---

## 1. The start day is fixed by the content, not by preference

`D1` must be a **Monday**. This is not a convention — three injects depend on it:

| Constraint | Source |
|---|---|
| `D5` is a Friday | Inject 05: *"The Friday deadline is real — the executive committee meets Monday"* · Inject 08: *"the deadline is Friday"* |
| `D3` is a Wednesday | Inject 09: *"Send me the pack Wednesday 09:00"* |
| `D4` is a Thursday | Inject 09: *"The board session is Thursday at 14:00"* |

Start on any other day and the in-world deadlines stop matching the real week,
which matters because several injects use the weekend deliberately — inject 08
lands at 16:30 on a Wednesday so its clock runs through it.

## 2. Dates

Two options. **Monday 12 October is recommended.**

| | Option A | Option B *(recommended)* |
|---|---|---|
| Week 1 | Mon 05 – Fri 09 Oct | **Mon 12 – Fri 16 Oct** |
| Week 2 | Mon 12 – Fri 16 Oct | **Mon 19 – Fri 23 Oct** |
| Week 3 | Mon 19 – Fri 23 Oct | **Mon 26 – Fri 30 Oct** |
| Week 4 | Mon 26 – Fri 30 Oct | **Mon 02 – Fri 06 Nov** |
| Board session | Thu 29 Oct, 14:00 | **Thu 05 Nov, 14:00** |

Option A is the nearest Monday to "two weeks". It leaves the consent chain —
data protection sign-off, forms issued, every intern replying, accounts and
access set up — with effectively **no slack**, and that chain runs through the
whole cohort in series. It gets longer as the cohort gets larger. If sign-off takes a week, forms reach interns after the
pilot has begun, and nobody may push anything until their form is recorded.

Option B costs a week and buys the whole chain a week of float. Take it unless
the date is fixed by something outside this programme.

Dates appear only in this section. Shifting the pilot is a change here and
nowhere else.

## 3. Before Week 1

The critical path is consent. Everything else can be done in an afternoon.

| Item | Owner | Blocks | Do it by |
|---|---|---|---|
| Consent policy signed off by the data protection contact | Programme lead | Everything below | **Immediately — this is the long pole** |
| Lawful basis and retention for assessment records decided | Data protection contact | Recording the first mark (~W1 D5 + 5 days) | Before W1 D5 |
| Consent forms issued to every intern | Programme lead | Any intern pushing anything | Within 2 days of sign-off |
| Forms returned and filed in the private repo | Interns | Repository access | 5 days before W1 D1 |
| Pseudonymous accounts created and handed over (Mode B) | Programme lead | First commit | 3 days before |
| Interns work through `INTERN-ONBOARDING.md`, fork, set git identity | Interns | First commit | 2 days before |
| Git author name and email verified for each intern | Mentor | First merge | Before first merge |
| Mentor reads all of `01-CLIENT`, `02-ARCHITECTURE`, `03-GRC`, `04-SOC` | Mentor | Answering in role | 3 days before |
| Mentor reads `Scenario-Key/` in the private repo | Mentor | Marking | Before W1 D5 |

**If sign-off slips**, start everyone in **Mode C** — private repository, nothing
published — and convert once consent lands. Mode C is the only reversible mode
and this is exactly the case it covers.

---

## 4. Week 1 — Baseline

Nothing looks like an incident. The material gathered this week is what both
teams need in week 3, and a team treating it as busywork will feel it.

| Day | Time | Event |
|---|---|---|
| **D1 Mon** | 09:00 | **Inject 01** — engagement letter · both teams |
| | | Joint half-day. The only session where all four work as one group |
| **D2 Tue** | — | **Due: engagement plan** → `06-DELIVERABLES/Engagement-Plan.md` |
| | 09:00 | **Inject 02** — audit handover · GRC |
| | 09:00 | **Inject 03** — SIEM health review · SOC |
| **D3 Wed** | | Work. Mentor answers in role |
| **D4 Thu** | | Work |
| **D5 Fri** | — | **Due: GRC** — asset, risk and supplier registers |
| | — | **Due: SOC** — detection surface, coverage gaps, detection backlog |

**Mentor:** ~1h/day in role, ~3h review across the week. Verify every intern's
git identity before merging their first PR.

---

## 5. Week 2 — First signals

| Day | Time | Event |
|---|---|---|
| **D1 Mon** | 08:40 | **Inject 04** — invoice phish · SOC |
| **D2 Tue** | | SOC investigating. GRC finishing week-1 carryover |
| **D3 Wed** | — | **Due: SOC** — `INC-01-Invoice-Phish.md` |
| | 14:00 | **Inject 05** — supplier breach notification · GRC |
| **D4 Thu** | | Work |
| **D5 Fri** | — | **Due: GRC** — Textway breach assessment + supplier register correction |

Release inject 04 at **08:40** if you can. It is written to arrive before the
day has settled, and how a team behaves when something lands before they are
ready is part of what is assessed.

**Mentor:** ~1–2h/day. Week-1 deliverables marked by now (5 working days from
merge).

---

## 6. Week 3 — Escalation

The heaviest week for both teams and for you.

| Day | Time | Event |
|---|---|---|
| **D1 Mon** | 07:15 | **Inject 06** — the runbook · SOC |
| **D2 Tue** | 11:00 | **Inject 07** — non-production data · **both, simultaneously** |
| **D3 Wed** | — | **Due: SOC** — INC-01 updated |
| | 16:30 | **Inject 08** — the regulatory clock · GRC |
| **D4 Thu** | — | **Due: GRC** — UAT DPIA · **Due: SOC** — impact reassessment |
| **D5 Fri** | — | **Due: GRC** — notification assessment |

**Inject 07 is the hinge.** Both teams receive the same email and neither has
the whole picture. One holds a compliance finding about a database, the other a
firewall log showing a connection to a database. **Do not help them find each
other.** If they do not connect it until the board pack, that is a legitimate
and instructive outcome.

**Inject 08 lands at 16:30 on Wednesday deliberately** so its clock runs over
the weekend. Do not soften it by releasing it Thursday morning.

**Mentor:** the heaviest week, ~2h/day. Both tracks are producing at once and
inject 08 carries the D4 integrity assessment.

---

## 7. Week 4 — Account

| Day | Time | Event |
|---|---|---|
| **D1 Mon** | 09:00 | **Inject 09** — board pack brief · both, one joint pack |
| **D2 Tue** | | Drafting |
| **D3 Wed** | 09:00 | **Due: board pack** → `07-FINAL/Board-Pack/`. The CISO does not edit it |
| | *rest of day* | **Mentor writes the Inject 10 questions from the submitted pack** |
| **D4 Thu** | 14:00 | **Board session** — 90 min: 60 present, 30 questions, **Inject 10** live |
| | *after* | Write up C3 and D4 immediately, before discussing with anyone |
| **D5 Fri** | | Individual summative feedback, one-to-one. D4 findings in person |
| | | Marking completed; moderation route decided |

**The Inject 10 questions cannot be written before Wednesday.** They target the
weakest claim each team actually made. Method and seed bank are in
`Scenario-Key/03-Board-Questions.md` in the private repository.

**Mentor:** ~6h across the week, concentrated Wednesday and Thursday.

---

## 8. Daily rhythm

| | |
|---|---|
| Injects release | At the stated time, in the working day |
| Mentor available in role | Whatever hours you commit to — say which, and keep them |
| PR review | Same day where possible; next working day at worst |
| Marking | Within 5 working days of merge, per the rubric |
| Formative feedback | In PR review. This is the main loop |

## 9. Mentor time

| Week | Estimate |
|---|---|
| Pre-pilot | 4h reading, 2h setup |
| Week 1 | 6–8h |
| Week 2 | 6–8h |
| Week 3 | 8–10h |
| Week 4 | 6h |
| Moderation and close | 3h |

**Roughly 35h for one mentor running it alone.** With three mentors that
divides, but not evenly and not to a third each — the natural split is one
mentor per track plus a moderator who marks neither, which loads the two track
mentors more heavily than the moderator during weeks 1 to 3 and reverses it in
week 4.

Agree the split before week 1 and write it down. Estimated from the materials;
this is the first run and nothing has been timed. Record what it actually
takes.

## 10. What slips gracefully, and what does not

**Can slip.** Intern deliverable deadlines — note the slip, mark it under D1,
carry on. Marking, within reason. The `protected-paths` ruleset import.

**Cannot slip.**

- **Inject release times.** Injects 04, 06 and 07 form one chain. If the SOC
  team stalls on 04, release 06 anyway — the incident does not wait for the
  responders, and a team discovering the first signal retrospectively at 06 is
  an instructive outcome, not a broken exercise.
- **The board session.** Fixed. The pack deadline is what makes it real.
- **Consent.** Nobody pushes until their form is recorded. No exceptions, and
  no starting someone "just on a branch" while their form is chased.

## 11. If something goes wrong

| Situation | Do |
|---|---|
| An intern drops out | Continue. The tracks are paired but a single intern can carry one; reduce scope, do not reduce standards |
| A mentor is ill in week 3 | No longer fatal — three mentors means cover exists. Hand over the track, and record the handover so marking allocation stays traceable. Only slip the schedule if two are out at once |
| A team is badly behind by week 3 | Let them arrive at the board underprepared. That is a real outcome and it is assessable. Do not do their work |
| Nobody connects inject 07 | Let it happen. Raise it in the debrief |
| An intern finds something genuinely serious | Inject 01 told them to escalate rather than save it. Respond in role, and mark it under D3 |
