# 03-GRC

**FinServe's existing governance material.** This is what the bank has today,
handed over by Internal Audit in [Inject 02](../05-INJECTS/Inject-02-Audit-Handover.md).

> **This is source material, not a model answer.** Nothing in this directory is
> an example of good practice. The Head of Internal Audit told you in writing
> not to rely on any of it, and he was being straight with you.

## Contents

| Path | Document | As at |
|---|---|---|
| `Asset-Register/` | [Asset register](Asset-Register/Asset-Register-2024.md) — 41 entries | March 2024 |
| `Risk-Register/` | [Risk register](Risk-Register/Risk-Register-Q3-2025.md) — 18 open risks | Q3 2025 |
| `Supplier-Register/` | [Supplier register](Supplier-Register/Supplier-Register-2025.md) — 63 suppliers | September 2025 |
| `Policies/` | [Policy register](Policies/Policy-Register.md) — 14 policies | Current |
| `Policies/` | [Information Security Policy v2.1](Policies/Information-Security-Policy-v2.1.md) | March 2023 |
| `Audit-Evidence/` | [2024 IT audit — findings and management responses](Audit-Evidence/IT-Audit-2024-Findings.md) | 2024, tracked to date |

## What you do with it

Your deliverables go in `06-DELIVERABLES/GRC/`, not here. This directory does
not change during the engagement — it is the state of the bank as you found it,
and the board pack will want to refer to it.

Read these before you rebuild anything. The registers are wrong in ways that
are informative: what a register omits tells you what the organisation was not
thinking about when it built it, and that is frequently a better finding than
the omission itself.

Two questions worth holding as you read:

1. **What question was this document built to answer?** The supplier register
   answers "when does the contract renew". It was never asked to answer "who
   holds our customers' data". That is not a filing error, it is a design
   decision made by a function that was not asked the second question.
2. **What has moved since it was written, and what has not?** Compare the dates
   on these documents against the change history in
   [`01-CLIENT/01-Company-Profile.md`](../01-CLIENT/01-Company-Profile.md) §3
   and against `02-ARCHITECTURE/`.

## A caution

It is easy to write a finding that says a register is incomplete. It is worth
more to say what the organisation could not see because of it, and what nearly
happened, or did happen, as a result.
