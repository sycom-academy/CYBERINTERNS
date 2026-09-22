# Intern Onboarding

Read this before you touch anything. It takes about twenty minutes to work
through and one step in it cannot be undone afterwards.

If you have never used git beyond `clone` and `commit`, that is fine and
expected. Follow it literally.

---

## 0. Before you start

You need three things:

| | |
|---|---|
| Your **participation mode** confirmed by the programme lead | A, B or C |
| A **GitHub account** — which one depends on your mode | see below |
| **Git installed** | `git --version` should print something |

**If you are in Mode C**, most of this does not apply to you. Skip to §8.

**If you are in Mode B**, the programme lead creates a pseudonymous account and
hands you the credentials. Use it for everything on this programme. Do not sign
in with your personal account by mistake — check the avatar in the top-right
before you push anything.

If you have not had your mode confirmed, stop and ask. Nobody pushes anything
until their consent form is recorded.

---

## 1. Set your git identity — do this first, it is permanent

Every commit you make records an author name and email **inside the commit
itself**. Those values are copied into every fork and every clone of this
repository, and no later rewrite removes them. If you get this wrong, your real
name and personal email are public permanently, whichever mode you chose.

**Do this before your first commit, not after.**

First, get your GitHub noreply address. Sign in to the account you will use,
then go to:

**https://github.com/settings/emails**

- Tick **Keep my email addresses private**
- Tick **Block command line pushes that expose my email**
- Copy the address shown — it looks like
  `12345678+yourhandle@users.noreply.github.com`

Then set git to use it:

```bash
git config --global user.name  "The name you want permanently public"
git config --global user.email "12345678+yourhandle@users.noreply.github.com"
```

Check it:

```bash
git config --global user.name
git config --global user.email
```

**Mode A** — use the name you are happy to have public forever.
**Mode B** — use your pseudonym, not your real name.

A mentor verifies this before your first pull request is merged. If it is
wrong, the fix is to start a fresh branch with corrected commits — the old
commits cannot be cleaned up once they are anywhere else.

---

## 2. Fork the repository

You do not have write access to `sycom-academy/CYBERINTERNS`, and you are not
meant to. You work in your own copy.

Go to **https://github.com/sycom-academy/CYBERINTERNS** and click **Fork**
(top right). Leave the name as it is. Fork to your own account — the one from
§0.

You now have `https://github.com/<your-handle>/CYBERINTERNS`.

This is why you cannot accidentally merge your own work: the permission simply
is not there. The review is not a formality you could skip if you wanted to.

---

## 3. Clone it and add the upstream remote

```bash
git clone https://github.com/<your-handle>/CYBERINTERNS.git
cd CYBERINTERNS
git remote add upstream https://github.com/sycom-academy/CYBERINTERNS.git
git remote -v
```

You should see four lines: `origin` pointing at **your** fork, `upstream`
pointing at **sycom-academy**.

- **`origin`** is yours. You push here.
- **`upstream`** is the programme's. You pull from here. You can never push to it.

---

## 4. Start a branch

Never work on `main`. One branch per deliverable.

```bash
git fetch upstream
git checkout -B main upstream/main
git checkout -b grc/ab/risk-register
```

Naming, from `REPO-GOVERNANCE.md`:

| Track | Pattern | Example |
|---|---|---|
| GRC | `grc/<initials>/<short-topic>` | `grc/ab/risk-register` |
| SOC | `soc/<initials>/<short-topic>` | `soc/tk/inc-01` |

Each inject tells you the branch name it expects. Use it.

---

## 5. Do the work, and commit as you go

Put files where the inject tells you — usually `06-DELIVERABLES/GRC/` or
`06-DELIVERABLES/SOC/`.

```bash
git add 06-DELIVERABLES/GRC/Risk-Register.md
git commit -m "Add risk register rebuilt from the architecture

Fourteen risks, scored on a 5x5 likelihood-impact scale stated in the
document. Three of FinServe's existing eighteen are not carried forward
because the architecture does not support them at the score recorded;
each is listed with the reason."
```

**Commit messages are assessed.** Criterion D1 in the rubric is your working
method, and a message that says *what changed and why* is worth more than
`update file`. Write the first line as a summary, leave a blank line, then
explain the reasoning. If you made a judgement call, say so — that is the part
a mentor most wants to see.

Commit often. Small commits are easier to review and easier to undo.

---

## 6. Push and open a pull request

```bash
git push -u origin grc/ab/risk-register
```

GitHub prints a link. Open it, or go to your fork and click **Compare & pull
request**.

Check the direction: **base** is `sycom-academy/CYBERINTERNS` `main`, **head**
is your fork and your branch.

The PR description template loads automatically. Fill it in properly — the
self-check is not decoration, and the **For the mentor** box at the bottom is
where you say what you were unsure about. Saying *"I could not decide whether
to treat this as a risk or an issue"* scores better than pretending you were
certain.

### Two automatic checks run

| Check | What it does |
|---|---|
| `gitleaks` | Scans for credentials in your files and in the history |
| `codeowners` | Validates the repository's own CODEOWNERS file |

Both must pass before anything can merge. If `gitleaks` fails on your PR, read
the annotation — it will point at a line. **Do not try to silence it.** There
is a marker in this repository that suppresses the scanner; it is for mentors
writing scenario material, and an intern using it on their own work is itself
a finding.

A mentor may need to approve the workflow run the first time you open a PR.
That is normal for a first-time contributor and is not you doing something
wrong.

---

## 7. Review, and keeping your fork current

A mentor reviews and leaves comments. Respond to every one — either change it,
or say why you disagree. **Disagreeing with a mentor, with a reason, is
explicitly fine and is marked as such.** Agreeing with everything is not a
strategy.

To make changes, commit to the same branch and push again. The PR updates
itself.

All review threads must be resolved before merge — that is enforced, not a
convention.

When it merges, it is squashed into a single commit on `main`. That is
deliberate: one commit per deliverable makes the week-4 assessment readable.

**Before starting the next deliverable**, refresh:

```bash
git checkout main
git fetch upstream
git reset --hard upstream/main
git push origin main
```

That resets your fork's `main` to match the programme's. Do it between
deliverables and you will avoid almost every merge conflict.

---

## 8. Mode C — working privately

You work in a private repository the programme lead sets up for you, not a
fork. Everything else is the same: branch per deliverable, commit with intent,
open a PR, respond to review.

Your assessment, feedback, mentor time and certificate are identical. You may
choose to publish later; that decision stays yours.

---

## 9. Things that will cause a problem

| Do not | Why |
|---|---|
| Commit a real credential, key or token | Push protection will block it, and if it gets through, gitleaks fails the PR. A real secret in history is a security incident, not a mistake |
| Use the scanner-suppression marker | Mentors only. Using it on your own work is a finding |
| Put a mark, score or feedback note in this repository | Those live in a separate private repository. If you are about to write one here, stop |
| Commit screenshots without checking them | Look at the whole image — tabs, notifications, filenames, the other monitor |
| Work directly on `main` | Branch. Always |
| Edit `00-ADMIN/`, `01-CLIENT/`, `02-ARCHITECTURE/`, `03-GRC/`, `04-SOC/` or `05-INJECTS/` | Mentor-owned. Raise a question instead — as a PR comment or to your mentor |
| Read ahead in `05-INJECTS/` | They release on a schedule. Reading ahead spoils the exercise for you, and you are the one it costs |

FinServe is fictional. Keep it that way — nothing about a real organisation,
a real system or a real person goes in here.

---

## 10. When something breaks

**"Updates were rejected because the remote contains work that you do not have"**
Your fork's `main` is behind. Run the refresh in §7.

**"Permission denied" pushing to `sycom-academy/CYBERINTERNS`**
You are pushing to `upstream`. Push to `origin` — your fork.

**Committed with the wrong name or email**
Stop immediately, do not push, and tell your mentor. Recoverable before a push,
much harder after.

**`gitleaks` failed and you do not understand why**
Read the annotation on the PR — it names the file and line. Ask your mentor
rather than guessing.

**Pushed to the wrong branch**
Not a disaster. Tell your mentor; it is fixable.

---

## 11. Where things are

| Path | What |
|---|---|
| `01-CLIENT/` | FinServe — who they are, how they are organised, what they do |
| `02-ARCHITECTURE/` | The estate: network, Azure, M365, data flows |
| `03-GRC/` | FinServe's existing registers, policies and audit findings |
| `04-SOC/` | FinServe's existing logs, alerts, detections and incidents |
| `05-INJECTS/` | What lands on you, and when |
| `06-DELIVERABLES/` | **Your work goes here** |
| `07-FINAL/Board-Pack/` | The week-4 board pack |
| `00-ADMIN/ASSESSMENT-RUBRIC.md` | **How you are assessed. Read it in week 1** |

Read the rubric early. It tells you what is marked, what is explicitly *not*
marked, and what the bar is. It is published so you can hold your mentor to it.

---

## 12. Asking for help

Ask. Early, and in the open.

Questions about the scenario go to your mentor, who answers in role as FinServe
staff. Questions about git, the repository or the process go to your mentor
directly.

Nobody is assessed on knowing this tooling already. You are assessed on the
work, on your reasoning, and on how you handle being wrong.
