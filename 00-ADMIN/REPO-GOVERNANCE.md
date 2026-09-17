# Repository Governance — SYCOM-CYBER-INTERNSHIP

Draft. Owner: CISO. Applies from pilot week 1.

## The constraint that shapes everything below

**GitHub cannot grant write access to a subdirectory.** Repository permissions
are whole-repo: anyone with `write` can modify every file in the tree. There is
no setting anywhere that makes `@interns-grc` able to write `03-GRC/` but not
`07-FINAL/Assessment/`.

So "each team writes only its own area" has to be built from three different
mechanisms, none of which is a permission:

| Intent | Mechanism | Strength |
|---|---|---|
| Interns cannot change `main` directly | Branch ruleset — PR required, 1 approval, no bypass | Hard block |
| A mentor sees every change before it lands | `CODEOWNERS` + "require code owner review" | Hard block |
| Assessment records are untouchable by interns | Push ruleset — restricted file paths, mentors bypass | Hard block |
| Interns stay in their own directories day to day | Convention + PR review | Social, not enforced |

The fourth row is the honest one. A GRC intern *can* open a PR touching
`04-SOC/`. They just can't merge it, because a mentor has to approve and will
see it. Accept that, or split into separate repositories per team — which costs
you the single board pack and the cross-team visibility the scenario depends on.

## Organisation structure

Move the repository off the `sycomsolutions` personal account into an
organisation. A personal account gives no teams, no role separation, and no
continuity if that account is lost.

**Org:** `sycom-academy`

| Team | Members | Repo role | Rationale |
|---|---|---|---|
| `@sycom-academy/ciso` | CISO | Admin | Owns assessment, certificates, settings |
| `@sycom-academy/mentors` | CISO + mentors | Maintain | Reviews and merges all intern work; cannot change repo settings |
| `@sycom-academy/interns-grc` | 2 GRC interns | Write | Opens PRs; cannot merge |
| `@sycom-academy/interns-soc` | 2 SOC interns | Write | Opens PRs; cannot merge |
| `@sycom-academy/observers` | Stakeholders, board-sim participants | Read | Week-4 audience |

Mentors get **Maintain**, not Admin, on purpose: it lets them merge and manage
issues without being able to disable the rulesets that make the assessment
evidence trustworthy. If a mentor can silently turn off branch protection, the
audit trail this repo exists to produce is worth less.

Interns are added to their team, never as direct collaborators. Direct
collaborators bypass team structure and are easy to forget at offboarding.

## Branch model

- `main` — protected. Only reachable by PR.
- `grc/<initials>/<short-topic>` — GRC intern working branches
- `soc/<initials>/<short-topic>` — SOC intern working branches
- `mentor/<short-topic>` — inject releases, scenario material

Branches are deleted on merge. Squash-merge only, so `main` reads as one commit
per deliverable — which is also what makes the week-4 assessment legible.

## Rulesets

Two rulesets, as JSON ready to import at
**Settings → Rules → Rulesets → New ruleset → Import a ruleset**.

### 1. `main-protection` (`.github/rulesets/main-protection.json`)

Targets the default branch. Requires a PR with one approving review, a code
owner review, resolution of all review threads, and dismissal of stale
approvals when new commits are pushed. Blocks deletion and force-push. Requires
linear history, which is why squash is the only permitted merge method.

`bypass_actors` is deliberately **empty**. The moment someone can bypass it,
the assessment record stops being evidence. If the CISO needs to make an
emergency change, they have Admin and can disable the ruleset explicitly —
which is logged, unlike a silent bypass.

### 2. `protected-paths` (`.github/rulesets/protected-paths.json`)

A push ruleset that blocks any push touching `00-ADMIN/`,
`07-FINAL/Assessment/`, `07-FINAL/Certificates/` or `.github/`, with
`@sycom-academy/mentors` as the only bypass actor. Also caps file size at 50 MB
and blocks credential file extensions at push time.

**Before importing**, replace `actor_id: 0` with the real numeric team id:

```
GET /orgs/sycom-academy/teams/mentors   -->   .id
```

Push rulesets are an organisation-repo feature and some rules are plan-gated.
Verify both import cleanly on your plan before relying on them; if
`file_path_restriction` is unavailable, the CODEOWNERS entry for `/07-FINAL/`
still forces CISO review, which is the weaker but workable fallback.

## Code owners

`.github/CODEOWNERS` routes every path to `@sycom-academy/mentors`, with
`07-FINAL/Assessment/` and `07-FINAL/Certificates/` reserved to
`@sycom-academy/ciso`.

Intern teams are **not** code owners of their own directories. If they were,
one GRC intern could approve the other's deliverable and satisfy the review
requirement without a mentor ever reading it. Peer review is valuable — add a
peer as a second reviewer, not as the gate.

## What this does not solve

- **Secrets pasted inside documents.** Push rulesets match filenames, and
  secret scanning does not read the inside of a `.docx` or a screenshot. The
  control here is the PR template checklist and the mentor actually looking.
- **Repository visibility.** None of the above matters if the repo is public.
  Confirm private before interns are added, and re-enable secret scanning and
  push protection afterwards — the free public-repo defaults do not carry over.
- **Offboarding.** Removing an intern from the team removes access going
  forward. Anything they cloned is already gone. Decide now whether that is
  acceptable for the FinServe material.
