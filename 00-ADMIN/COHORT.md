# Current Cohort

**This is the only file that changes between runs.** Everything else in the
repository is written against "the cohort", "each track" and "the mentors"
rather than against numbers, so a new intake is an edit here and nowhere else.

If you find a hardcoded headcount anywhere else, it is a defect — fix it and
point it at this file.

---

## This run

| | |
|---|---|
| Cohort | Pilot 1 |
| Scenario | Scenario 1 — FinServe Digital Bank Ltd |
| Length | 4 weeks |
| Week 1, Day 1 | *to be fixed — see [`WEEKLY-SCHEDULE.md`](WEEKLY-SCHEDULE.md) §2* |
| Board session | W4 D4, 14:00 |

### Tracks

| Track | Interns | Team |
|---|---|---|
| GRC | 3 | `@sycom-academy/interns-grc` |
| SOC | 4 | `@sycom-academy/interns-soc` |
| **Total** | **7** | |

Seven puts this run in the 5–8 band of the sizing guidance below. For this run
that means:

- **Pairs.** SOC works as two pairs. GRC, with three, works as one pair plus
  one intern who takes the pair's alternate deliverables and reviews theirs.
  Rotate who is on their own at each deliverable, so nobody spends all four
  weeks unpaired
- **Cohort lead and deputy.** Named: a lead from GRC and a deputy from SOC.
  The lead coordinates work across both tracks, including the rotation of the
  solo role, and is the mentors' first point of contact. The deputy covers when
  the lead is unavailable. Names are in the private roster
- **Board pack editors.** Named: a lead editor from GRC, who has the final
  say on structure, the lead story and cuts, and a deputy from SOC, who owns
  findings consolidation and the check that every claim traces to a source.
  Names are in the private roster. Both must be in mode A or B, because the
  pack's commit history is public
- **Joint half-day (Inject 01).** Above six it stops working as one session.
  Split by track, then converge
- **Mentor ratio.** GRC has three interns per track mentor. SOC has four,
  which is at the limit. One more SOC intern needs a second SOC mentor

Names and contact details are not recorded here. This repository is public.

### Mentors

| Role | Count | Notes |
|---|---|---|
| Track mentor — GRC | 1 | Marks GRC A-criteria |
| Track mentor — SOC | 1 | Marks SOC A-criteria |
| Moderator | 1 | Marks neither track; moderates both |
| **Total** | **3** | `@sycom-academy/mentors` |

Record the actual allocation before week 1 — who marks which criteria — and
keep it here. Rubric §7 requires it to be agreed in advance and written down.

### Observers

Stakeholders and board-session participants: `@sycom-academy/observers`, read
access, added for week 4.

---

## Sizing guidance

The scenario material scales further than the operational model does. Injects
are addressed to **a track**, not to a headcount, so they work unchanged for
any track size. What does not scale for free is below.

| Cohort size | Works? | What changes |
|---|---|---|
| 2–4 interns | Yes, as written | Nothing |
| 5–8 interns | Yes | Split each track into pairs; pairs take alternate deliverables and review each other's before it reaches a mentor. Board pack needs a named editor |
| 9–12 interns | Strained | Run two cohorts through the same scenario in parallel rather than one large one. Two board sessions |
| 13+ | No | Not with this model. The board pack is one joint document and the coordination cost grows faster than the cohort |

**Mentor ratio.** One track mentor per track, plus a moderator who marks
neither — three is the minimum for independent moderation and it is what rubric
§7 assumes. Above roughly **four interns per track mentor**, pull request review
stops fitting in the hours the role brief estimates, and a second mentor on that
track is needed rather than optional.

**The binding constraint is the board pack, not the mentors.** Inject 09 makes
it a single joint deliverable assessed as one document. Four authors can write
one document. Ten cannot, and the failure is not visible until week 4 when
there is no time to recover. If the cohort is larger than eight, split it.

## Things that change with cohort size

| Item | Where | What to reconsider |
|---|---|---|
| Individual adjustment range | Rubric §4, currently ±0.5 bands | Larger teams make free-riding easier to hide. Widen the range, or mark more criteria individually |
| Joint deliverables | Rubric §4 — C2, C3, D2, D3 marked once for all | With two cohorts, marked once per cohort |
| The joint half-day | Inject 01 | Above ~6 people it stops being a working session. Split by track, then converge |
| Board session length | Inject 09 — 90 minutes | Fixed. More presenters means less time each, not a longer session |
| Consent chain duration | [`WEEKLY-SCHEDULE.md`](WEEKLY-SCHEDULE.md) §3 | Scales with headcount. More people to chase, same deadline |

## After each run

Record what actually happened, so the next cohort is planned on evidence rather
than on the estimates in the role brief:

| | Estimated | Actual |
|---|---|---|
| Mentor hours, total | ~35h for one; less each across three | |
| Deliverables submitted late | — | |
| Interns completing (band 3+ in every criterion) | — | |
| Marker variance found at calibration | — | |
| Time lost to the fork workflow | — | |
