# Mentor Guide

How to run it. Not what happens when — that is
[`WEEKLY-SCHEDULE.md`](WEEKLY-SCHEDULE.md) — and not how to mark, which is
[`ASSESSMENT-RUBRIC.md`](ASSESSMENT-RUBRIC.md).

This is the part that is hard: playing a character, reviewing without solving,
and holding a list of answers you must not give away.

---

## 1. You are the teacher and the examiner, and those conflict

Every instinct you have as a mentor is to help. Every requirement you have as
an assessor is evidence of what they would do unaided.

You cannot satisfy both by being careful. You satisfy them by changing **how**
you help:

| Instinct | What it costs | Do instead |
|---|---|---|
| "The supplier register should have a DPA column" | You have made the finding. They record it | "What question would a DPO ask this register that it cannot answer?" |
| "This timeline is missing the SharePoint downloads" | Same | "Walk me through what the attacker knew at 08:30 that they did not at 07:52" |
| Rewriting a paragraph in review | You wrote their deliverable | Quote it back and say what a reader would take from it |
| "Good catch" on a planted weakness | Confirms a list exists and that they are on it | "Noted — what follows from it?" |

**Point at the gap. Do not fill it.** A question that makes them look again
teaches more than the answer and leaves the assessment intact.

This gets harder in week 3 when a team is visibly struggling. That is the point
at which it matters most.

## 2. Answering in role

Questions about the scenario go to you, and you answer **as FinServe staff**,
not as a mentor wearing a name badge.

### The cast, and how each behaves

| Who | Stance when asked |
|---|---|
| **Priya Raman**, CISO | Candid, wants the review to land. Will say when something embarrasses her. Your default voice |
| **Marcus Ifill**, SecOps Manager | Overloaded, straight, slightly defensive about the SIEM because he has raised things twice. Helpful if asked precisely |
| **Adeola Balogun**, Cloud Platform Lead | Volunteers uncomfortable facts unprompted. Treat that candour as scarce |
| **Daniel Whitcombe**, Internal Audit | Ally. Wants his open findings actioned. Will not oversell his own function |
| **Elliot Vance**, CTO | Defensive about Lighthouse. The control uplift was descoped on his call |
| **Chinelo Nwosu**, GC and DPO | Careful, stretched, wearing two hats. Slow to answer because she is |
| **Sarah Lindqvist**, COO and interim CRO | Capacity-limited. Will tell you she has not had time |
| **Nadia Ferreira**, Head of Finance Ops | Owns the settlement process. Knows it works, not why it is built that way |
| **Gavin Marsh**, CEO | Commercial. Do not soften him — inject 08 depends on him being exactly as written |

Full detail is in [`../01-CLIENT/04-Stakeholders.md`](../01-CLIENT/04-Stakeholders.md).

### Rules for in-role answers

1. **Characters do not know everything.** Marcus does not know what two of the
   custom rules do — he says so in inject 03. If asked again, he still does not
   know. Do not quietly upgrade a character's knowledge because the answer would
   be useful.
2. **Some characters are unhelpful, realistically.** A vendor takes five working
   days. Corebridge logs come by ticket. Chinelo is on leave. That friction is
   scenario content, not an obstacle to route around.
3. **If the scenario does not cover it, invent consistently and write it down.**
   Interns will ask things nobody anticipated. Answer plausibly, then record it
   in `Scenario-Key/` so the next mentor gives the same answer. Two mentors
   contradicting each other is worse than either answer.
4. **Never answer out of role to be kind.** "Well, between us, what you actually
   want to look at is…" ends the exercise.
5. **State which hat you are wearing** when you switch. "As Priya:" and "As your
   mentor:" are different conversations and they should look different.

## 3. Reviewing a deliverable

Pull request review is the main teaching loop. It is also public to the cohort,
so keep it about the work.

**What a good review comment does**

- Names what a reader would conclude, and why that differs from what was meant
- Asks for the evidence behind a claim, rather than asserting it is wrong
- Distinguishes a required change from a suggestion, explicitly
- Says when something is good, specifically — "the split between what you can
  prove and what you cannot is exactly right" teaches more than "nice work"

**What does not belong in a PR comment**

- Anything evaluative about the person — that goes in `Feedback/`
- A mark, a band, or a comparison to another intern
- Anything from `Scenario-Key/`, including confirming a finding is "the one"

**Approving.** You are a code owner and your approval is required. Approve when
the deliverable is sound enough to be assessed, not when it is perfect — a
deliverable with a weakness you have pointed out and they have chosen not to
change is a legitimate submission and a legitimate finding about them.

**Timing.** Same day where possible, next working day at worst. A team blocked
on review cannot work, and the schedule has no slack for it.

## 4. Releasing injects

Release at the stated time, in the working day. Several land deliberately
awkwardly — inject 04 at 08:40, inject 06 at 07:15, inject 08 at 16:30 on a
Wednesday so its clock runs through the weekend. **Do not tidy those up.** How a
team behaves when something arrives before they are ready is assessed.

**If a team is behind, release anyway.** Injects 04, 06 and 07 are one chain.
The incident does not wait for the responders, and a team discovering the first
signal retrospectively at 06 is an instructive outcome, not a broken exercise.

**Inject 07 is the hinge.** Both teams get the same email and neither has the
whole picture. One holds a compliance finding about a database, the other a
firewall log showing a connection to a database. **Do not help them find each
other.** If they never connect it, that is a real finding about cross-team
working, and it is marked under D2.

## 5. You know the answers — the tier C boundary in practice

`Scenario-Key/` in the private repository holds the weakness key, the incident
ground truth and per-inject guidance. Holding it changes how you must speak.

- **Do not confirm a finding.** "Yes, that is the one" tells them a list exists.
  Acknowledge neutrally and ask what follows from it.
- **Do not steer toward one they have missed.** If they miss the UAT database
  entirely, they miss it, and the board pack shows it.
- **Do not paste anything from it into a PR comment**, including a phrase.
- **Add to it.** When an intern finds something not in the key, write it in. The
  key is not exhaustive and a finding outside it is usually a good one.

The key exists so you can follow their reasoning, not so you can score hits. If
you find yourself counting how many they found, re-read rubric §1.

## 6. Marking, day to day

Detail is in the rubric. Three things that go wrong in practice:

1. **Mark criterion by criterion, across all interns** — not one person's whole
   set. Marking a person at once produces halo effects; this is the single
   biggest control you have.
2. **Write the rationale before the band.** Reversing it rationalises a number
   already chosen.
3. **Calibrate before you start.** All mentors mark the same deliverable
   independently, then compare band by band. Disagreement here is cheap.
   Disagreement found at moderation is expensive and too late to be fair.

Mark within five working days of merge, while you still remember the review.

## 7. The hard moments

**An intern names Rachel Oduya as the cause.** She clicked; the conditions that
let a stolen session token work are not hers. Say so directly, in review and in
person. This is assessed under D4 and it is the finding most likely to appear
in the board session rather than in writing.

**A team reaches the wrong conclusion, confidently.** Do not correct it. Ask
what evidence would change their mind. If the answer is "nothing", that is the
finding.

**A team is badly behind by week 3.** Let them arrive at the board
underprepared. It is a real outcome and it is assessable. Reducing scope is
legitimate; reducing standards or doing their work is not.

**An intern pushes back on your review and is right.** Say so, change your
position, and say what changed it. The rubric tells them disagreement with a
reason is marked well — that only stays true if you behave as though it is.

**Someone asks whether they are passing.** Point at the rubric and the marks
they already have. Do not reassure, and do not withhold.

**An intern is struggling personally.** Stop being a mentor and be an employer.
Escalate to the programme lead. Nothing in this document outranks that.

## 8. What not to do

| Never | Why |
|---|---|
| Rescue a silence in the board session | Ten seconds is long in a board room and how they use it is the assessment |
| Confirm or deny during the board session | Debrief afterwards |
| Do the work, however small | You have written their deliverable |
| Answer as yourself when you meant to answer in role | Ends the exercise |
| Discuss one intern with another | It is personal data and it poisons the cohort |
| Put a mark or feedback note in the public repository | Tier B. It goes in the private repo |
| Skip calibration because someone joined late | That is exactly when variance creeps in |

## 9. When to escalate to the programme lead

- Anything about an intern's welfare, capability to continue, or conduct
- A consent question, or an intern wanting to change participation mode
- A data protection question you are not certain about
- A suspected breach of the tier C boundary, including your own slip
- Disagreement between mentors about a mark that calibration did not resolve

Escalating early is free. A mark defended for three weeks and then changed is
not.

## 10. After the pilot

Fill in the "After each run" table in [`COHORT.md`](COHORT.md) while it is
fresh. Record what the mentoring actually cost in hours, what the interns found
that the key did not have, what the calibration exercise turned up, and which
injects worked.

This is the first run. Some of it will not work, and the person who notices is
useful.
