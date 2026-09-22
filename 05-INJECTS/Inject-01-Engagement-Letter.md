# Inject 01 — Engagement letter

**Release:** Week 1, Day 1, 09:00 · **Team:** Both · **Deliverable due:** W1 D2

---

## The artefact

> **From:** Priya Raman, Chief Information Security Officer, FinServe Digital Bank Ltd
> **To:** Sycom Consulting — Project Sentinel team
> **Date:** W1 D1
> **Subject:** Engagement scope — cyber and data protection assurance review
>
> Good morning, and welcome.
>
> I will keep this short because you will get plenty of detail from the
> material we have shared.
>
> FinServe is a UK digital bank. We hold a PRA authorisation and are
> dual-regulated by the PRA and the FCA. We have about 450 staff, 180,000
> retail customers, and an estate that is mostly in Azure with a legacy
> footprint in Slough that we have been trying to close since 2023.
>
> The board has asked for independent assurance. I want to be straight with
> you about why. We have had two years of rapid change — a core banking
> migration, a cloud programme, an acquisition — and the honest position is
> that our control environment has not kept pace with our architecture. I do
> not have a specific incident driving this. I have a feeling that we would
> not like what a determined look would find, and I would rather find it than
> have someone else find it for us.
>
> You have four weeks. Two workstreams:
>
> **Governance, risk and compliance.** I need to know what we have, what it is
> worth, what could go wrong with it, and who else is holding our data. We have
> registers. I do not trust them. Start from the architecture and build what
> you think they should say.
>
> **Security operations.** I need to know what we would actually see. We bought
> Sentinel in 2024 and I have been told it is "fully deployed" more than once.
> I want to know which of our systems could have something bad happen to them
> without anyone finding out, and how long we would have to notice.
>
> You will present to the board in week four. The audience is four
> non-executives, a chief executive who is commercially minded and impatient,
> and me. Two of the non-executives sit on the audit committee and will have
> read your pack properly. Assume they have not read anything else.
>
> What I want in week four is not a list of everything wrong. It is: what
> should we fix first, what will it cost us not to, and what do we have to
> tell somebody about.
>
> Ask us questions. If you find something that worries you before week four,
> do not sit on it until the presentation.
>
> Priya Raman
> CISO, FinServe Digital Bank Ltd
> p.raman@finserve.example

---

## What you are asked to produce

**Both teams, jointly — one document.**

A short engagement plan, no more than two pages:

1. **Scope.** What you will cover in four weeks and, more importantly, what you
   will not. A scope that claims everything is a scope that commits to nothing.
2. **Approach.** How each workstream will work, and the two or three points
   where you will need to compare notes.
3. **Assumptions and dependencies.** What you are taking as given, and what you
   need from FinServe. Be specific — "access to logs" is not a dependency,
   "read access to the Sentinel workspace by W1 D3" is.
4. **Questions.** Things the material does not answer that you need answered.
   These go to your mentor, who will respond in role.
5. **Deliverables and dates.** What lands when.

You have the architecture in `02-ARCHITECTURE/` and the client profile in
`01-CLIENT/`. You do not have anything else yet. Say what else you need.

## Where it goes

`06-DELIVERABLES/Engagement-Plan.md`, via a PR from a branch named
`grc/<initials>/engagement-plan` or `soc/<initials>/engagement-plan` —
agree between you who opens it, and add the other pair as reviewers.

## Time budget

Half a day, both teams together. This is the only inject where you are expected
to work as one group.

## Note

The CISO's last line is not decoration. If you find something serious in week
two and save it for the board in week four, that is a finding about you, not
about FinServe.
