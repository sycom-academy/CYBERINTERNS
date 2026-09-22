# Assessment Framework and Marking Scheme — v1

Owner: CISO. Applies to the four-week pilot. **Interns should read this before
week 1 and may refer to it at any point.**

Publishing the criteria is what makes the marks defensible. If a mark cannot
be explained by reference to something in this document, it is not a mark, it
is an opinion.

---

## 1. What this assesses, and what it does not

This assesses **how you work**, not **what you found**.

That distinction is deliberate and it has a consequence you should understand:
**this document does not contain a list of expected findings, and it never
will.** The scenario has things in it to be found. Listing them here would hand
you the answers, and marking against a list would reward recognition over
reasoning.

So the descriptors below describe the quality of an argument, not its
conclusion. A team that misses something significant but reasons well about
what it did find scores better than a team that names the right issue with no
support.

### Not assessed

- **Finding everything.** Nobody is expected to. Four weeks, four people.
- **Prior knowledge of UK financial services regulation.** You are expected to
  look things up and cite them accurately. You are not expected to arrive
  knowing SS2/21.
- **Code or query that executes.** KQL that does not run loses nothing. KQL
  against a log source that is not collected loses a great deal — that is a
  reasoning error, not a syntax error.
- **Speed.** Meeting the in-scenario deadlines matters. Being first does not.
- **Volume.** A 40-page register is not better than a 12-page one. Several
  criteria below actively reward leaving things out.
- **Agreeing with your mentor.** A well-argued position your mentor disagrees
  with scores full marks.

---

## 2. Scale

Every criterion is marked on the same four-band scale.

| Band | Name | Meaning |
|---|---|---|
| 4 | **Strong** | Would stand up in front of a real audit committee with light supervision |
| 3 | **Competent** | Sound work. Meets the standard for successful completion |
| 2 | **Developing** | Right direction, material gaps in rigour, evidence or judgement |
| 1 | **Not yet** | Does not meet the standard; the gap is one of approach, not polish |

**Band 3 is the bar.** Completion requires band 3 or above in every criterion
and an overall weighted score of 3.0 or above. Band 4 is genuinely difficult
and is not expected across the board.

A band 1 in criterion D4 (integrity) is not offset by strength elsewhere. See §5.

---

## 3. Criteria and weighting

| Group | Weight |
|---|---|
| **A** — Domain craft (track-specific) | 35% |
| **B** — Evidence and reasoning | 25% |
| **C** — Communication and audience | 20% |
| **D** — Professional judgement and integrity | 20% |

### A — Domain craft, GRC track

**A1 · Registers and models (15%)**
Whether the asset, risk and supplier registers are usable instruments rather
than documents. Granularity chosen and justified. Scoring scale stated and
applied consistently. Risks written as cause, event and consequence rather than
as topics. Coverage traceable to the architecture.

> **4** — Registers a real second line would adopt. Granularity is argued, not
> assumed. Risks that do not survive contact with the evidence are removed as
> readily as new ones are added.
> **3** — Complete, consistent, traceable. Scoring applied evenly.
> **2** — Broadly right, but granularity is arbitrary, scoring drifts, or
> coverage has unexplained gaps.
> **1** — A list of topics with scores attached.

**A2 · Regulatory application (10%)**
Whether obligations are applied to these facts rather than recited. Correct
instrument, correct test, correct conclusion — and the reasoning visible
between them.

> **4** — Applies the right test to the right facts and reaches a conclusion
> that would survive challenge. Distinguishes what the law requires from what
> is prudent.
> **3** — Correct instruments, correctly applied, conclusions supported.
> **2** — Cites the right regimes but reasons generically; conclusions asserted
> rather than derived.
> **1** — Quotes regulation without applying it, or applies the wrong one.

**A3 · Assessment under uncertainty (10%)**
Breach assessments, DPIAs and notification decisions made on incomplete facts.
Whether the decision is defensible on what was known at the time.

> **4** — Reaches a clear position, states the facts it turns on, and says what
> would change it. Defensible to a regulator after the fact.
> **3** — Clear position, supported, with material uncertainties named.
> **2** — Reaches a position but the reasoning does not carry it, or hedges
> where a decision was required.
> **1** — No position, or a position contradicted by the team's own evidence.

### A — Domain craft, SOC track

**A1 · Detection and coverage analysis (15%)**
Whether the detection surface and coverage work describes what is actually
seen, distinguishes collection from retention from alerting, and ranks gaps by
consequence.

> **4** — Someone could act on it directly. Gaps expressed as what an adversary
> could do unobserved, not as missing connectors.
> **3** — Accurate, complete, consequence-ranked. Collection, retention and
> alerting kept distinct.
> **2** — Largely accurate but conflates the three, or ranks by ease of fix.
> **1** — An inventory of log sources.

**A2 · Investigation and analysis (10%)**
Timeline construction, control-failure analysis, scoping. Whether each step is
tied to an artefact.

> **4** — Timeline is evidence-anchored throughout. Control failures explained
> mechanically — what each control did and why it did not stop this.
> **3** — Accurate timeline, evidence cited, scope reasoned.
> **2** — Timeline broadly right but steps asserted without artefacts, or scope
> stated without reasoning.
> **1** — Narrative unsupported by the evidence provided.

**A3 · Scoping the unknown (10%)**
Whether the team distinguishes what it can prove, what it assesses as likely,
and what it cannot rule out — and whether it says which unanswerable questions
are unanswerable because of a control gap.

> **4** — The three categories are explicit and correctly populated. The
> "cannot rule out" category grows when it should. Attributes each gap to
> absent telemetry or expired retention, correctly.
> **3** — Distinguishes the categories and sustains the distinction.
> **2** — Acknowledges uncertainty in general terms without structuring it.
> **1** — States conclusions the evidence does not support.

### B — Evidence and reasoning (both tracks)

**B1 · Traceability (10%)**
Every factual claim traces to an artefact, a document or a named assumption.

> **4** — Traceable throughout, including in the summary. Assumptions labelled
> as assumptions at the point of use.
> **3** — Claims supported; assumptions identified.
> **2** — Supported in the detail, asserted in the summary.
> **1** — Unattributed claims, or invented facts.

**B2 · Proportionality (8%)**
Whether conclusions are as strong as the evidence and no stronger. Both
over-claiming and excessive hedging lose marks.

**B3 · Prioritisation (7%)**
Whether findings are ordered by consequence and the ordering is defended.
Everything-is-critical and everything-is-medium are the same failure.

### C — Communication and audience (both tracks)

**C1 · Written deliverables (8%)**
Structure, precision, economy. Whether a reader finds what they need.

**C2 · Board pack (7%)**
Whether it answers the three questions the CISO asked in Inject 09, is pitched
at the room described there, and survives a reader who checks the page where
the evidence is weakest.

**C3 · Live presentation and questions (5%)**
The board session, including Inject 10. Holding a sound position under
pressure; changing it explicitly when given new information; stating the limits
of knowledge without hedging; handing over to whoever actually knows.

> Answering everything confidently scores lower than answering two-thirds well
> and declining the rest accurately.

### D — Professional judgement and integrity (both tracks)

**D1 · Working method (6%)**
Use of the repository as intended: branches, PRs, review, squash merges.
Commits and PR descriptions that explain intent. Responsiveness in review.

**D2 · Collaboration (5%)**
Within and across tracks. Whether the two workstreams found the places their
work connected — and whether they did so without being told to.

**D3 · Escalation (4%)**
Whether significant findings were raised when found rather than saved for the
presentation. Inject 01 makes this explicit.

**D4 · Integrity under pressure (5%)**
Whether conclusions hold when a stakeholder would prefer a different one, and
whether they move when given genuine new information rather than social
pressure. Whether gaps are filled with evidence or with plausibility.

> **4** — Gives an uncomfortable answer clearly and early, with reasoning the
> recipient can act on. Concedes readily to evidence, not to seniority.
> **3** — Maintains sound positions under pressure; does not invent.
> **2** — Softens conclusions to suit the audience, or over-hedges to avoid
> committing.
> **1** — Changes a conclusion to please, presents an assumption as a fact, or
> conceals a gap.

---

## 4. Team and individual marks

Deliverables are team products. Marks are not.

**Team mark** — each criterion is marked once per track against the submitted
deliverables. Criteria C2, C3, D2 and D3 are marked once for all four interns,
since the board pack and the cross-track work are joint.

**Individual adjustment** — up to ±0.5 bands, from evidence, applied by the
moderator.

The evidence is the repository. The branch-per-deliverable and
squash-merge-per-deliverable model exists partly for this: `git log`, PR
authorship and review comment threads show who did what, who reviewed whom, and
how someone responded to challenge. That record is contemporaneous and neither
mentors nor interns can revise it afterwards.

An adjustment is recorded with its reasons or it is not applied.

**Nobody is marked down for their teammates' work** except where D2 is the
finding — a team that did not function is a team finding.

---

## 5. The D4 floor

A band 1 in D4 is not averaged away.

If an intern presents an assumption as a fact, conceals a gap, or changes a
conclusion because a senior person wanted it changed, that is recorded as a
band 1 in D4 and the overall outcome is *not yet competent* regardless of the
weighted score. It is recoverable, it is discussed directly, and it is the one
thing in this framework that does not trade off against anything else.

This is the profession's core requirement. A GRC analyst who tells the business
what it wants to hear, or a SOC analyst who states a conclusion the logs do not
support, is worse than no analyst, because both are believed.

---

## 6. Mapping: deliverables to criteria

| Deliverable | Inject | Primary criteria |
|---|---|---|
| Engagement plan | 01 | C1, D2 |
| Asset / risk / supplier registers | 02 | A1 (GRC), B1, B3 |
| Detection surface, coverage gaps, backlog | 03 | A1 (SOC), B1, B3 |
| Incident report INC-01 | 04, 06 | A2 (SOC), A3 (SOC), B1, B2 |
| Textway breach assessment | 05 | A2 (GRC), A3 (GRC), B2 |
| UAT DPIA | 07 | A2 (GRC), A3 (GRC), B1 |
| Incident impact reassessment | 07 | A3 (SOC), B2, D2 |
| Notification assessment | 08 | A3 (GRC), B2, **D4** |
| Board pack | 09 | C2, B3, D3 |
| Board session | 09, 10 | C3, **D4** |

Criteria D1 and D2 are assessed continuously across all deliverables.

---

## 7. Process

**Marking.** Each deliverable is marked by a mentor within five working days of
merge. Marks and written feedback are recorded in the private
`SYCOM-INTERNSHIP-ASSESSMENT` repository. **No mark, score, feedback note or
moderation comment enters this repository at any point.**

**Moderation.** Two marks are awarded: independent moderation, or, where there
is only one marker, the single-marker protocol below.

*Two or more mentors.* All final marks are moderated by a mentor who did not do
the original marking, and signed off by the CISO. Moderation checks consistency
between the two tracks — the two A-criteria sets are different instruments and
must be calibrated against each other, not just internally.

*One mentor.* Independent moderation is impossible and nothing substitutes for
it. What follows reduces the two errors a single marker is most prone to —
drift across a cohort, and the halo effect where a strong impression on one
criterion colours the rest — and makes the marks auditable afterwards:

1. **Mark by criterion, not by person.** Mark criterion A1 for every intern,
   then A2, and so on. Marking a person's whole set at once is what produces
   halo effects; this is the single most effective control available to one
   marker.
2. **Write the rationale before the band.** For each mark, write the sentence
   that justifies it against a named descriptor, then award the band. Reversing
   that order rationalises a number already chosen.
3. **Blind re-mark a sample.** After all marking is complete, wait at least 48
   hours, then re-mark two deliverables without reference to the original
   marks. A band's difference on either is a signal of drift; investigate
   rather than average.
4. **Mark the tracks in a fixed order and record it.** Drift is directional,
   so the order matters and must be known when the marks are reviewed.
5. **Deferred moderation.** Marks are recorded as **provisional**. They become
   final when either a second mentor moderates them, or the CISO signs them off
   having read the rationales against this document. Certificates are not
   issued against provisional marks.
6. **Say so.** Interns are told at the start that the pilot runs with a single
   marker, what that means, and what the protocol is. Their right of challenge
   below matters more, not less, under single marking.

An external moderator — the co-source audit firm, or an assessor from another
programme — satisfies the "two or more mentors" route and does not have to be a
FinServe mentor or hold repository access. Sending anonymised deliverables and
the rationales is sufficient.

**Feedback.** Formative feedback is given in PR review as work is merged. That
is the fastest loop available and it is the main one. Summative feedback is
given individually in week 4 after the board session.

**Challenge.** An intern may challenge any mark by asking which descriptor it
was awarded against and why. If the answer cannot point at this document, the
mark changes. This is not an appeals process with forms; it is a conversation
the marker should be able to have on the spot.

---

## 8. Open dependencies

Recorded honestly rather than assumed:

1. **Independent moderation requires a second marker.** The `mentors` team has
   one member. §7 now carries a single-marker protocol so the framework is
   operable, and marks awarded under it are **provisional** until either a
   second mentor moderates them or the CISO signs them off against the
   rationales. Certificates are not issued against provisional marks. An
   external moderator satisfies this without needing repository access, and is
   the cheaper route if a second mentor is not close.
2. **Lawful basis and retention for assessment records** must be decided before
   the first mark is recorded. Flagged in the private repository's README.
3. **Inject 10 questions** are written from the submitted board pack on W4 D3
   and do not exist in advance.
4. **This is v1 and has never been run.** The weightings are a judgement, not a
   calibration. Expect to revise after the pilot, and record what changed.
