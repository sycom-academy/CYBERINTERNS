# Joining and Leaving

How someone is added to the programme, what they get, and what happens when
they leave. One section per role.

Cohort size and the current allocation are in [`COHORT.md`](COHORT.md).

---

## 1. Teams and what each one gets

Five teams. Nobody is ever added to a repository as a direct collaborator —
always through a team, because direct collaborators bypass the structure and
are the thing everybody forgets at offboarding.

| Team | `CYBERINTERNS` (public) | `SYCOM-INTERNSHIP-ASSESSMENT` (private) | Tier C scenario key |
|---|---|---|---|
| `ciso` | Admin | Write | Yes |
| `mentors` | Write | Write | **Yes** |
| `interns-grc` | **None** — fork and PR | None | No |
| `interns-soc` | **None** — fork and PR | None | No |
| `observers` | Read | None | No |

Intern teams hold **no write access** to the public repository. They fork it
and open pull requests. That is what prevents an intern merging their own
deliverable — access, not a rule that has to be configured correctly. See
[`PROGRAMME-ARCHITECTURE.md`](PROGRAMME-ARCHITECTURE.md) §4.1.

The intern teams still exist even though they grant nothing on either
repository. They are how you know who is in the cohort, and they are what gets
emptied at offboarding.

## 2. Adding a mentor

Approved by the CISO. A mentor sees the scenario key and every intern's
assessment record, so this is not a low-trust addition.

| # | Step | Done by |
|---|---|---|
| 1 | Check the disqualifier: **no personal relationship with a participating intern**. See [`MENTOR-ROLE-BRIEF.md`](MENTOR-ROLE-BRIEF.md) | CISO |
| 2 | Invite to the `sycom-academy` organisation | CISO |
| 3 | **Confirm they accepted.** An invitation is not membership, and a pending invite grants nothing | CISO |
| 4 | Add to `@sycom-academy/mentors` | CISO |
| 5 | Confirm `CODEOWNERS` still resolves — `/repos/{owner}/{repo}/codeowners/errors` should return `{"errors":[]}` on both repos | CISO |
| 6 | Point them at the role brief, the rubric, and this file | CISO |
| 7 | They read `01-CLIENT`, `02-ARCHITECTURE`, `03-GRC`, `04-SOC` and the injects | Mentor |
| 8 | They read `Scenario-Key/` in the private repo | Mentor |
| 9 | They take part in the **calibration exercise** — rubric §7 — before any of their marking counts | All mentors |
| 10 | Record the marking allocation in [`COHORT.md`](COHORT.md) | CISO |

Step 9 is not optional and not a formality. A mentor who starts marking without
calibrating is the marker-variance problem the rubric exists to prevent.

**Mid-cohort additions.** Possible but do step 9 against deliverables already
submitted, not against a fresh one — you are calibrating them to the standard
already being applied, not establishing a new one.

## 3. Adding an intern

Nobody is added until their consent form is recorded. No exceptions, including
starting someone "just on a branch" while the form is chased.

| # | Step | Done by |
|---|---|---|
| 1 | Consent policy signed off by the data protection contact — **once, before any intake** | Programme lead |
| 2 | Brief them on the three participation modes **before** they commit to the programme | Programme lead |
| 3 | They complete [`Consent-Form.md`](Consent-Form.md) individually, in writing | Intern |
| 4 | Form filed in the private `SYCOM-CONSENT-RECORDS` repository. Mode recorded there and nowhere mentors can read | Programme lead |
| 5 | **Mode B:** create the pseudonymous account and hand it over | Programme lead |
| 6 | Invite to the organisation; add to `interns-grc` or `interns-soc` | Programme lead |
| 7 | They work through [`INTERN-ONBOARDING.md`](INTERN-ONBOARDING.md) — fork, remotes, **git identity** | Intern |
| 8 | **Verify their git author name and email before their first PR merges** | A mentor |
| 9 | Record the verification in `SYCOM-CONSENT-RECORDS` | Programme lead |

Step 8 is the one that cannot be fixed afterwards. `user.name` and `user.email`
are written into every commit object and survive into every fork and clone; a
pseudonymous account is worth nothing if the commits carry a real name. Check
it, do not ask whether they did it.

An intern who returns no form is in **Mode B**. Silence is never read as
consent to publication under a real name.

## 4. Adding an observer

Low-trust and low-effort. Observers see the public repository, which is public
anyway — the team exists so that board-session invitations and any future
private material have a list to work from.

| # | Step | Done by |
|---|---|---|
| 1 | Invite to the organisation | Programme lead |
| 2 | Add to `@sycom-academy/observers` | Programme lead |
| 3 | Send the board session details and the pack once it is published | Programme lead |

Observers get **no** access to the private repository, and never to the
scenario key. A board-session participant who has read the answers is not
playing the role the session needs.

## 5. Leaving

Offboarding is where access models rot. Do it on the day, not at the end of the
cohort.

### An intern leaves or finishes

| # | Step |
|---|---|
| 1 | Remove from `interns-grc` / `interns-soc` |
| 2 | Remove from the organisation if they are in no other team |
| 3 | Their **fork stays theirs.** It is their work and they may keep it |
| 4 | Their merged work stays in `main`. It is published and cannot be withdrawn — this was disclosed on the consent form |
| 5 | If they ask for their assessment record to be deleted, honour it in full. The record is deletable; the published work is not |
| 6 | Ask once whether they want to change participation mode — C to A or B is possible, A or B to C is not |

### A mentor leaves

| # | Step |
|---|---|
| 1 | Remove from `@sycom-academy/mentors` — this removes access to both repositories and to the scenario key in one action |
| 2 | Remove from the organisation if they are in no other team |
| 3 | Confirm `CODEOWNERS` still resolves on both repositories |
| 4 | **Reassign their marking.** Any criterion they had not finished goes to another mentor, who calibrates against what was already marked rather than starting fresh |
| 5 | Record the handover in `Moderation/` — marking allocation has to stay traceable, or the marks stop being defensible |
| 6 | They have read the scenario key. That cannot be undone, and it is a reason to be careful at step 2 of §2 rather than a problem at offboarding |

### At the end of a cohort

| # | Step |
|---|---|
| 1 | Empty `interns-grc` and `interns-soc` |
| 2 | Empty `observers` |
| 3 | Leave `mentors` and `ciso` as they are |
| 4 | Fill in the "After each run" table in [`COHORT.md`](COHORT.md) |
| 5 | Record in `Moderation/` that the cohort is closed and marks are final |

## 6. What is never granted

- **Interns: write access to `CYBERINTERNS`.** The fork model depends on this.
  Granting it does not break anything immediately, which is what makes it
  dangerous — it removes a control silently.
- **Interns or observers: any access to `SYCOM-INTERNSHIP-ASSESSMENT`.** It
  holds marks about identifiable people and the scenario answers.
- **Anyone: direct collaborator access to either repository.** Always a team.
- **Observers: the scenario key.** See §4.

## 7. Verifying the access model

Run this after any change to teams or membership. It is the check that would
have caught the two failures this programme has already had — a `CODEOWNERS`
routing to a team that did not exist, and a team with no repository access.

```bash
for R in sycom-academy/CYBERINTERNS sycom-academy/SYCOM-INTERNSHIP-ASSESSMENT; do
  echo "$R"
  gh api "repos/$R/codeowners/errors" --jq '.errors | length'   # want 0
done
```

`0` on both means every team named in `CODEOWNERS` exists, is visible, and
holds write access. Anything else means the review model is not enforcing what
the documents say it does, and it will fail silently rather than loudly.
