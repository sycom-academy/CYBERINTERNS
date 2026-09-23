# Consent and Publication

Owner: Sycom Academy programme lead. Applies before any intern pushes anything.

> **Not legal advice.** This is a working policy drafted from the UK GDPR and
> the Data Protection Act 2018. It was signed off by Sycom Academy's data
> protection contact on 2026-09-23.
>
> Note that the Data Protection Officer named in the scenario is a fictional
> character. The controller here is **Sycom Academy**, and the interns are
> **real people**. Nothing in `01-CLIENT/` applies to this document.

---

## 1. The problem, stated plainly

This repository is going public. When it does, each participating intern's
GitHub handle, commit history, and every deliverable they write becomes
world-readable and search-indexable. Forks, clones, archives and caches survive
any later change of mind.

Two things follow that the original governance note did not address.

**Consent must be freely given.** A person who wants a training placement, is
asked by the organisation providing it to agree to publication, and can see
that everyone else agreed, is not in a position to refuse freely. If declining
carries any cost — visibility, friction, a worse experience, or just being the
one who said no — the consent is weak. Article 7(4) and Recital 43 are
explicit that consent is not valid where there is a clear imbalance between the
parties, and a training provider and an unpaid intern is exactly that.

**Withdrawal cannot be honoured.** Article 7(3) requires that withdrawing
consent be as easy as giving it. Once this repository is public, it is not
possible to withdraw. Forks are outside the controller's reach, search engines
cache, and third-party archives exist. Deleting the repository does not undo
publication.

Consent that cannot be withdrawn is a poor basis for processing. It is used
here anyway, because the alternatives are worse and because the interns are the
people whose interests the basis exists to protect. But the limitation is
disclosed up front rather than discovered later, and the design below is built
so that refusing costs nothing.

## 2. Three participation modes

Every intern chooses one. **Pseudonymous is the default**, so that appearing
under a real name is an active opt-in rather than a norm to deviate from.
Nobody is told what anyone else chose.

| | **Mode A — Attributed** | **Mode B — Pseudonymous** *(default)* | **Mode C — Private** |
|---|---|---|---|
| Work is public | Yes | Yes | No |
| Real name and handle public | Yes | No | No |
| GitHub account used | Their own | A pseudonymous account created for the programme | Their own |
| Where work lives | Fork of the public repo | Fork of the public repo | Private repo, mentor-reviewed |
| Assessment | Identical | Identical | Identical |
| Certificate | Identical | Identical | Identical |
| Mentor review and feedback | Identical | Identical | Identical |
| Portfolio value | Direct — a public record with their name on it | Indirect — they can privately prove authorship to an employer | None from this repo |
| Reversible later? | **No** | Partly — linking the pseudonym to themselves is their choice, and is theirs alone to make | Yes — they may publish later if they wish |

Modes B and C are not lesser options and must not be presented as such. The
assessment, the feedback, the certificate and the mentor's time are identical
in all three. Mode B in particular gives a full public record of the work with
the identity withheld, and an intern in Mode B can show any employer the
account is theirs whenever they choose.

**Mode C is the only reversible choice**, and a mode C intern can move to A or B
at the end if they want to. A and B cannot be undone.

## 3. What is published, precisely

In modes A and B:

- Every file they commit to `06-DELIVERABLES/` and `07-FINAL/`
- Every commit message they write
- Every pull request title, description and review comment
- The commit author name and email recorded in git metadata (see §4)
- Their GitHub account handle, avatar and profile as linked from those commits
- Timestamps, which reveal working patterns

Not published, in any mode: marks, written feedback, moderation notes,
certificates, the consent record itself. Those are personal data held in the
private assessment repository and never enter this one.

## 4. Git metadata — the part that is easy to get wrong

A pseudonymous GitHub account does not help if git is configured with a real
name and personal email. Those values are written into every commit object and
are permanent — rewriting history after the fact does not remove them from
forks or from anyone's existing clone.

Before the first commit, every intern in mode A or B must set:

```
git config user.name  "<the name they want permanently public>"
git config user.email "<their GitHub noreply address>"
```

The noreply address is found in GitHub under **Settings → Emails → Keep my
email addresses private**, and looks like `12345678+handle@users.noreply.github.com`.
The same settings page has **Block command line pushes that expose my email**,
which should be enabled.

This is checked by a mentor before the first push is merged. It is the single
most common way an intended pseudonym is broken, and it cannot be fixed
afterwards.

## 5. How consent is taken

1. **Brief before enrolment, not after.** The three modes are explained in
   writing before an intern commits to the programme, so the choice is not made
   under pressure of having already started.
2. **Individually, in writing.** Each intern completes
   [`Consent-Form.md`](Consent-Form.md). No group sign-off, no verbal
   agreement, no assumed consent from silence or from a ticked enrolment box.
3. **Choice is private.** Modes are recorded by the programme lead. Mentors are
   told only what they need to operate — which repository a given intern works
   in. Interns are never told what others chose.
4. **No default drift.** An intern who does not return a form is in mode B.
   Absence of a form is never treated as consent to publication under a real
   name.
5. **Before any push.** No intern pushes to any repository until their form is
   recorded.
6. **Revisit at the end.** After the board session, each intern is asked once
   whether they want to change mode. Moving from C to A or B is possible.
   Moving from A or B to C is not, and they are reminded of that.

## 6. Where the record lives

Completed forms are personal data about identifiable people. They go in the
**private** `SYCOM-INTERNSHIP-ASSESSMENT` repository under `Consent/`, never in
this one.

| | |
|---|---|
| Lawful basis for the consent record itself | Legal obligation — Article 7(1) requires the controller to demonstrate consent |
| Retention | Duration of the programme plus six years |
| Access | Programme lead and mentors |

## 7. Data subject rights

Interns retain their rights regardless of mode. Every rights request goes to
Sycom Academy's data protection contact at hello@sycomsolutions.com. In
practice:

| Right | Position |
|---|---|
| Access | Honoured in full |
| Rectification | Honoured for the assessment record. A published commit cannot be altered without rewriting history, which does not reach forks |
| Erasure | Honoured in full for the private assessment record. **For published content, the repository can be made private or deleted, but this does not reach forks, clones, caches or archives.** This limitation is disclosed on the consent form |
| Objection / withdrawal | Recorded and acted on so far as it is possible to act. See the erasure position above |
| Portability | The work is theirs. They may copy it anywhere |

The honest summary given to interns is: *anything in the private repository can
be deleted on request; anything published cannot reliably be unpublished.*

## 8. Under 18s and other considerations

If any participant is under 18, this policy does not cover them — publication
of a child's personal data needs a separate assessment and, depending on age,
parental authorisation. Do not enrol an under-18 into mode A without taking
advice.

Interns who are not UK residents may have rights under another regime. Take
advice rather than assuming this policy transfers.

## 9. Open items

1. ~~**Sign-off** by Sycom Academy's data protection contact.~~ Resolved:
   signed off on 2026-09-23 with no changes requested. The Pilot 1 forms had
   gone out a few hours earlier; they match the signed-off version, so nobody
   re-signs.
2. **A privacy notice** under Articles 13 and 14 covering the programme as a
   whole — enrolment, assessment, publication and retention. This document
   covers publication only, and is not a substitute for the notice.
3. **Retention period for the assessment records themselves** — flagged in the
   private repository's README and still undecided.
4. ~~**A named contact** for rights requests, to appear on the form.~~
   Resolved: Sycom Academy's data protection contact, hello@sycomsolutions.com,
   shown in §7 and on the form.
5. **Mode C and the joint board pack.** Inject 09 makes the board pack a single
   joint deliverable across the whole cohort, and `07-FINAL/Board-Pack/` is
   public. A mode C intern cannot commit to it without appearing in its history.
   The workable answer is that a mentor commits the joint pack on the team's
   behalf, so the document is published with no per-author attribution — which
   costs the attributed interns something they may have chosen mode A to get.
   Decide this before the forms go out, because the answer changes what mode A
   is worth and therefore what the choice means. It is not decided here.
