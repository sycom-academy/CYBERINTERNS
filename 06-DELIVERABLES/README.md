# 06-DELIVERABLES

**Your work goes here.** Everything else in this repository is either source
material you were given or administration. This is the one directory the
cohort writes to, and it is what gets marked.

> **Filenames are not a matter of taste here.** Each inject names the exact
> file its deliverable goes in, several injects revise a file an earlier inject
> created, and the board pack is assembled from these paths. A deliverable
> under a different name is a second copy of a document that already exists,
> not a new one — and nobody notices until two versions of the same register
> reach the board.

## The rule

1. **Use the filename the inject gives you.** It is in the inject's
   *Where it goes* section. Do not improve it, shorten it, or add your name,
   the date or a version number.
2. **Every deliverable is Markdown, and the filename ends in `.md`.** A file
   with no extension, or a `.docx`, does not render on GitHub — a mentor
   opening it to mark it gets raw text or a download prompt.
3. **If you are revising, edit the existing file.** Do not create
   `INC-01-v2.md` or `Risk-Register-updated.md`.
4. **Nothing else goes in this directory.** Notes, drafts, screenshots and
   working files stay out. If a deliverable needs evidence, link to it.

Uploading through the browser is the usual way the extension gets lost. If you
drag a file in, check the name in the commit box before you commit it.

## What goes where

| Inject | Path | Who |
|---|---|---|
| [01](../05-INJECTS/Inject-01-Engagement-Letter.md) | `Engagement-Plan.md` | **Both tracks, one file.** Agree between you who opens it |
| [02](../05-INJECTS/Inject-02-Audit-Handover.md) | `GRC/Asset-Register.md` | GRC |
| [02](../05-INJECTS/Inject-02-Audit-Handover.md) | `GRC/Risk-Register.md` | GRC |
| [02](../05-INJECTS/Inject-02-Audit-Handover.md) | `GRC/Supplier-Register.md` | GRC · revised by inject 05 |
| [03](../05-INJECTS/Inject-03-SIEM-Health-Review.md) | `SOC/Detection-Surface.md` | SOC |
| [03](../05-INJECTS/Inject-03-SIEM-Health-Review.md) | `SOC/Coverage-Gaps.md` | SOC |
| [03](../05-INJECTS/Inject-03-SIEM-Health-Review.md) | `SOC/Detection-Backlog.md` | SOC · revised by inject 04 |
| [04](../05-INJECTS/Inject-04-Invoice-Phish.md) | `SOC/INC-01-Invoice-Phish.md` | SOC · revised by injects 06 and 07 |
| [05](../05-INJECTS/Inject-05-Supplier-Breach.md) | `GRC/Textway-Breach-Assessment.md` | GRC |
| [06](../05-INJECTS/Inject-06-Mailbox-Access.md) | `SOC/INC-01-Evidence-Requests.md` | SOC |
| [07](../05-INJECTS/Inject-07-UAT-Data-Discovery.md) | `GRC/UAT-Data-DPIA.md` | GRC |
| [08](../05-INJECTS/Inject-08-Regulatory-Clock.md) | `GRC/Notification-Assessment.md` | GRC |

Twelve files for the whole engagement. If you are about to create a thirteenth,
check the inject again.

The engagement plan sits at the top of this directory rather than under a track,
because inject 01 asks for **one** plan covering both. The board pack is not
drafted here — see [`07-FINAL/README.md`](../07-FINAL/README.md).

## Branch and pull request

Branch from `main` as `<track>/<initials>/<short-name>`, using the name the
inject gives:

```
grc/<initials>/textway-breach
soc/<initials>/inc-01
```

You do not have write access to this repository. Fork it, push the branch to
your fork, and open the pull request against `sycom-academy/CYBERINTERNS`
`main`. The steps are in
[`INTERN-ONBOARDING.md`](../00-ADMIN/INTERN-ONBOARDING.md), or
[`BROWSER-WORKFLOW.md`](../00-ADMIN/BROWSER-WORKFLOW.md) if you are working
without git installed.

**One submission per team per inject.** Rotate who opens it, add the other
pair as reviewers, and say in the pull request who wrote which part. Where
your work is in a private repository, your mentor reviews it instead of your
partner.

Fill in the pull request template, including the AI use section. Nobody is
marked down for using AI or for saying so; see
[`ASSESSMENT-RUBRIC.md`](../00-ADMIN/ASSESSMENT-RUBRIC.md) §1.

## Revising a deliverable

Four of the twelve files are revised by a later inject. When that happens:

- Edit the existing file in place.
- Add the new material as a new section rather than rewriting what is there,
  unless the inject tells you a previous conclusion was wrong.
- Say in the pull request what changed and why. A reviewer should not have to
  diff the file to find out.
- If the new inject contradicts something you concluded earlier, **say so
  explicitly in the file.** Changing an answer silently reads as if you never
  held the first one.

## What a mentor checks first

Before the content, on every pull request:

- The file is at the path the inject names, with `.md` on the end.
- It is the right directory for the track.
- No real credentials, keys or customer data — FinServe and Textway are
  fictional, and nothing from your own employer belongs here.
- Screenshots have been checked for what is visible in the background.
- Your git author name and email match what was recorded at onboarding. The
  `commit-identity` check runs on every pull request and will tell you if not.
