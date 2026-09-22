# Mentor Role Brief

Owner: CISO.

> **Recruitment is done.** `mentors` has three members. This is now an
> onboarding brief — what the role involves, what it costs in hours, and what
> disqualifies someone — and remains the reference for the next cohort.
> §3's option B, external moderator only, is no longer needed.

---

## Why this role exists

Written while the programme had one mentor, to explain what a second would
unblock. All three are now resolved, and they are the reason the role matters:

1. **Independent moderation of marks.** A single marker's judgements can be made
   auditable; they cannot be made independent. With three mentors a moderator
   who did not do the original marking is available, and marks are final rather
   than provisional.
2. **Independent review of intern work.** The person who wrote the scenario no
   longer has to be the person who reviews and marks it.
3. **Continuity.** One mentor was a single point of failure over four weeks.
   Three is cover.

What three mentors introduce instead is **marker variance** — see
[`ASSESSMENT-RUBRIC.md`](ASSESSMENT-RUBRIC.md) §7. Calibrate before marking.

## What the role is not

- Not a full-time commitment
- Not a requirement to write scenario material — that is done
- Not a requirement to be a FinServe or Sycom employee
- Not a requirement to hold admin rights on anything
- Not a requirement to be present for all four weeks, if the role is scoped to
  moderation only (see the two options below)

## Two ways to fill it

### Option A — Full second mentor

Shares the running of the pilot. Reviews deliverables, answers interns in role,
marks, moderates, attends the board session.

**Unblocks all three items above.** This is the better outcome.

### Option B — External moderator only

Moderates the marks at the end. Needs no repository access, no involvement
during the four weeks, and no knowledge of the scenario beyond the rubric. Is
sent anonymised deliverables, the marks, and the written rationales, and checks
that each mark is supported by the descriptor it was awarded against.

**Unblocks item 1 only** — but item 1 is the one that gates certificates.

A co-source audit firm, an assessor from another training programme, or a peer
CISO can do this. It is roughly a day of work.

## What a full second mentor does

| Activity | When | Estimate |
|---|---|---|
| Read the scenario material before week 1 | Before start | 4h |
| Release injects on schedule (10 injects) | Throughout | 2h total |
| Answer intern questions **in role** as FinServe staff | Daily, ad hoc | 1–2h/week |
| Review PRs — 15 deliverable paths plus a 6-section board pack | Throughout | 3–4h/week |
| Mark against 16 criteria per track | Rolling, within 5 working days of merge | 6h total |
| Moderate the other marker's marks | Week 4 | 3h |
| Board session, including writing the Inject 10 questions from the submitted pack | Week 4 | 4h |

**Roughly 25–30 hours across five weeks**, weighted towards weeks 3 and 4.
These are estimates from the materials, not from a completed run — this is the
first pilot and nothing here has been timed.

## What the person needs

**Essential**

- Working knowledge of **either** UK financial services GRC **or** security
  operations — not both. The two tracks are marked with separate instruments,
  and a mentor strong in one can moderate the other against written criteria.
- Enough git and GitHub to review a pull request and leave line comments.
- Willingness to give a direct answer to an intern who is wrong, and to change
  their own position when an intern is right.

**Desirable**

- Experience assessing or supervising junior analysts
- Familiarity with UK GDPR, the Money Laundering Regulations 2017, or the PRA
  and FCA operational resilience framework
- Incident response experience, for the week-3 material

**Disqualifying**

- Any personal relationship with a participating intern. The assessment is a
  record about an identifiable person and moderation is the control that makes
  it defensible; a moderator who knows a candidate socially cannot provide it.

## What they get access to

| | Full mentor | External moderator |
|---|---|---|
| `CYBERINTERNS` (public content repo) | Write, via `@sycom-academy/mentors` | Public read |
| `SYCOM-INTERNSHIP-ASSESSMENT` (private) | Read/write | Anonymised extracts only |
| Tier C scenario key | Yes | The rubric only |
| GitHub org membership | Yes | Not required |

## The two things to do on day one

For a full mentor, both are required before the framework is fully operable:

1. Add them to `@sycom-academy/mentors`. The team holds **Write** on
   `CYBERINTERNS` and CODEOWNERS resolves against it. An invitation is not
   membership — check they have accepted.
2. Grant them access to `SYCOM-INTERNSHIP-ASSESSMENT`, where the marks and the
   tier C scenario key live. The `mentors` team already has Write there.
3. Have them read the scenario material and `Scenario-Key/` before week 1, and
   take part in the calibration exercise in rubric §7 before any marking
   counts.

## Honest summary for a candidate

A four-week simulated engagement for a small cohort, split GRC and SOC, against a
fictional UK digital bank with a deliberately imperfect estate. The scenario,
injects, client dossier and marking framework are written; the work is running
it and assessing it. Around 25–30 hours. First run, so some of it will not work
and the person who spots that is useful.
