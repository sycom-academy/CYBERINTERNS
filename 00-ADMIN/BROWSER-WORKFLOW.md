# Working in the browser: one page

Everything on this page is done on github.com. You do not need git, a terminal
or a code editor. It is the same workflow as
[`INTERN-ONBOARDING.md`](INTERN-ONBOARDING.md), with clicks instead of
commands. Use whichever you are comfortable with, but do not mix the two on
the same branch.

New to GitHub? Do the free **Introduction to GitHub** course first, from
GitHub Skills (**https://skills.github.com**), or directly at
**https://github.com/skills/introduction-to-github**. It takes about an hour
and practises the same steps as below on a repository of your own.

---

## 1. Before anything else (once)

- [ ] Signed in to the right account. Check the avatar, top right. Mode B
      interns use the account the programme lead gave you.
- [ ] **https://github.com/settings/emails**: tick **Keep my email addresses
      private** and **Block command line pushes that expose my email**. With
      the first box ticked, everything you commit in the browser uses your
      noreply address. Without it, your personal email goes into the commit
      and the `commit-identity` check fails your pull request.
- [ ] **https://github.com/settings/profile**: the **Name** field is the name
      you are happy to have public forever (mode A) or your pseudonym (mode B).
      Your merged work on `main` is credited to this name.

## 2. Fork (once)

Go to **https://github.com/sycom-academy/CYBERINTERNS**, click **Fork** (top
right), leave the name as it is, and click **Create fork**. You now have your
own copy at `github.com/<your-handle>/CYBERINTERNS`. Do all your work there.

If you were told to work in a private repository instead, skip this step and
do everything below in that repository.

## 3. Start a branch (once per deliverable)

1. On your fork, if you see **This branch is X commits behind**, click
   **Sync fork**, then **Update branch**. This brings your copy up to date.
   This is the only time you click **Update branch** yourself.
2. Click the branch button that says **main** (top left of the file list).
3. Type the branch name the inject gives you, for example
   `grc/ab/risk-register`, and click **Create branch: … from main**.
4. Check the branch button now shows your branch name, not `main`. Never work
   on `main`.

## 4. Add your deliverable

1. Still on your branch, open the folder the inject names, usually
   `06-DELIVERABLES/GRC` or `06-DELIVERABLES/SOC`.
2. Click **Add file**, then either:
   - **Create new file**: type the file name (for example
     `Risk-Register.md`) and write in the box. **Preview** shows how it will
     look.
   - **Upload files**: drag in a file you wrote elsewhere. Before you do,
     look at every screenshot for names, tabs, notifications and anything else
     in the background.
3. Click **Commit changes…**. In the box that opens:
   - **Commit message**: one line saying what changed.
   - **Extended description**: why, and any judgement call you made. Commit
     messages are assessed (rubric criterion D1). `Add files via upload` on its
     own scores nothing.
   - Choose **Commit directly to the `<your branch>` branch**. If it says
     `main`, stop: go back to step 3.

To change a file later, open it on your branch, click the pencil icon, edit,
and commit the same way. Commit as often as you like.

## 5. Open the pull request

1. On your fork, click **Contribute**, then **Open pull request** (or the
   yellow **Compare & pull request** banner).
2. Check the line at the top: **base repository:** `sycom-academy/CYBERINTERNS`,
   **base:** `main` ← **head repository:** your fork, **compare:** your branch.
3. Fill in the description template. The **For the mentor** box is where you
   say what you were unsure about.
4. Click **Create pull request**.

Three automatic checks run: `gitleaks` (secrets), `codeowners` (the
repository's own reviewer file) and `commit-identity` (every commit uses a
noreply address). If `commit-identity` fails, go back to section 1, then ask
your mentor: the fix is a fresh branch. The first time, a mentor may need to
approve the checks before they run. That is normal.

## 6. Respond to review

- Your mentor comments on the **Files changed** tab. Reply to every comment:
  either change the work, or say why you disagree. Disagreeing with a reason is
  marked as a strength.
- To change the work, edit the file on **your branch** in your fork (section 4)
  and commit. The pull request updates itself. Do not open a new one.
- Do not click **Update branch** or **Resolve conversation** on the pull
  request unless your mentor asks you to. Your mentor resolves each thread when
  they are satisfied.
- Never merge. You cannot merge into the programme repository, and that is
  deliberate: a mentor merges after approving.

When it is merged, start the next deliverable from section 3.

---

Stuck? Ask your mentor, in the pull request or directly. Nobody is assessed on
knowing GitHub already.
