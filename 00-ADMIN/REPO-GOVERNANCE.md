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

## Two repositories, not one

The controls this programme needs — branch protection, rulesets, native secret
scanning — are **free on public repositories and paid on private ones**. Rather
than pay for a four-week pilot, the content is split by sensitivity:

| Repository | Visibility | Holds | Who can see it |
|---|---|---|---|
| `CYBERINTERNS` | **public** | Scenario material, intern deliverables, board pack | Everyone |
| `SYCOM-INTERNSHIP-ASSESSMENT` | **private** | Marks, feedback, moderation notes, certificates | CISO + mentors |

The line is **criteria public, results private**. The rubric and marking scheme
stay in `00-ADMIN/` where interns can read them — publishing the criteria is
what makes the marks defensible. Only records about an identifiable person move
to the private repo.

This is better governance than one private repo, not just a cheaper one. The
people being assessed should not share a permission boundary with their own
assessment records. Splitting them makes that structural rather than a matter
of everyone remembering which directory is sensitive.

`07-FINAL/Assessment/` and `07-FINAL/Certificates/` have been removed from this
repository accordingly. `07-FINAL/` now holds the board pack only.

### Consent is a prerequisite, not a formality

Making this repo public means every intern's commits, name, GitHub handle and
work product are permanently world-readable, and forks and mirrors survive any
later change of mind.

This note originally said to get written consent and offer an alternative to
anyone who declines. That framing was wrong in one respect and it matters:
it makes publication the norm and declining a deviation. An intern who can see
that public is the default, and that opting out marks them out, is not refusing
freely — and consent that is not freely given is not consent.

The policy is now in [`CONSENT-AND-PUBLICATION.md`](CONSENT-AND-PUBLICATION.md)
and the form in [`Consent-Form.md`](Consent-Form.md). Three participation modes,
with **pseudonymous as the default**, so appearing under a real name is an
active opt-in. Assessment, feedback, mentor time and certificate are identical
in all three.

The other thing that note did not say: **withdrawal cannot be honoured.** Once
this repository is public, forks and caches are beyond reach, so an intern who
changes their mind cannot be put back. That limitation is disclosed on the form
rather than discovered afterwards.

## Organisation structure

Move both repositories off the `sycomsolutions` personal account into an
organisation. A personal account gives no teams, no role separation, and no
continuity if that account is lost. GitHub Free for organisations is
sufficient — there is nothing to pay.

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

A push ruleset that blocks any push touching `00-ADMIN/` or `.github/`, with
`@sycom-academy/mentors` as the only bypass actor. Assessment paths are absent
because assessment records are not in this repository at all. Also caps file size at 50 MB
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

`.github/CODEOWNERS` routes every path to `@sycom-academy/mentors`.

Intern teams are **not** code owners of their own directories. If they were,
one GRC intern could approve the other's deliverable and satisfy the review
requirement without a mentor ever reading it. Peer review is valuable — add a
peer as a second reviewer, not as the gate.

## Secret scanning

Two layers, because they catch different things.

**GitHub native secret scanning with push protection** is free on public
repositories, and this repository is public. Enable it at Settings -> Code
security. Push protection is stronger than anything in CI: it rejects the push
itself, so the credential never lands in any branch.

**gitleaks in CI** (`.github/workflows/secret-scan.yml`) runs on every pull
request into `main` and every push to `main`. It is not redundant — it unpacks
Office documents, which GitHub's scanner does not do.

Three scans run per job, any one of which fails the check:

1. **Working tree** — every file as it stands.
2. **Unpacked Office documents** — `.docx`, `.xlsx`, `.pptx`, `.odt`, `.ods`,
   `.odp` are zip archives of XML. gitleaks reads text, so a credential pasted
   into a Word evidence pack is invisible to a normal scan. The job unzips them
   first and scans the extracted XML. This was verified against a test `.docx`:
   missed before unpacking, caught after.
3. **Git history** — `--log-opts=--all`, so a secret added and then deleted in
   a later commit is still caught.

All scans run with `--redact`, so the secret itself never appears in CI logs.
Reports upload as a build artifact with 30-day retention.

### How this differs from the real thing

gitleaks fires **after** the push to a working branch, not before it. GitHub's
push protection rejects the push itself. So a credential caught here already
exists in that branch's history and **must still be rotated** — the check only
guarantees it never reaches `main`. Tell interns this explicitly; "CI caught
it" is not the same as "no harm done".

### Deliberately fake credentials in injects

A SOC inject may need a realistic-looking key in it — triaging a leaked
credential is a legitimate exercise. Mark the line `SIM-FAKE` and
`.gitleaks.toml` will allow it. This is a mentor tool. An intern adding
`SIM-FAKE` to silence a finding on their own deliverable is itself a finding.

### Making it a required check

Once the workflow has run at least once, add `gitleaks` to the required status
checks in the `main` ruleset (Settings -> Rules -> main-protection -> Require
status checks to pass). Until then it reports but does not block.

### Maintenance

`GITLEAKS_VERSION` is pinned in the workflow. Bump it deliberately; a floating
version means CI changes underneath you mid-pilot. The workflow installs the
gitleaks binary from its GitHub release rather than using `gitleaks-action`,
which requires a paid licence for organisation-owned repositories — which is
where this repo is heading.

## What this does not solve

- **Secrets inside images.** The Office unpacking above handles `.docx` and
  `.xlsx`, but a credential visible in a screenshot is just pixels. No scanner
  in this setup reads it. The control is the PR template checklist and the
  mentor actually looking at the image.
- **Repository visibility.** This repo is public by design. That is only safe
  because assessment records live elsewhere and because every intern has
  consented. Both conditions must hold before anyone is added.
- **Offboarding.** Removing an intern from the team removes access going
  forward. Anything they cloned is already gone. Decide now whether that is
  acceptable for the FinServe material.
