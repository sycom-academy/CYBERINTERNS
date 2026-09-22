# Inject 07 — What is in the test environment

**Release:** Week 3, Day 2, 11:00 · **Team:** Both, simultaneously · **Deliverable due:** W3 D4

---

## Artefact 1 — a reply to a week-1 question

> **From:** Adeola Balogun, Cloud Platform Lead
> **To:** Project Sentinel — GRC workstream; Project Sentinel — SOC workstream
> **Cc:** Priya Raman
> **Date:** W3 D2, 10:54
> **Subject:** RE: Query — UAT refresh, what is masked?
>
> Apologies, this has been sitting in my drafts since last week.
>
> You asked what the nightly UAT refresh masks. Short answer: names and email
> addresses. That is it.
>
> Longer answer, because I would rather you had it from me than found it.
>
> The refresh takes a copy of the production database and runs a masking
> script. The script replaces forename, surname and email with generated
> values. Everything else comes across as it is in production: account
> numbers, sort codes, balances, full transaction history, dates of birth,
> addresses, and National Insurance numbers.
>
> The reason is reconciliation testing. The UAT test pack reconciles balances
> and transaction sets against known production figures, and if you mask the
> financial data the tests stop meaning anything. We raised it during
> Lighthouse. The decision at the time — and I was in the room — was that UAT
> sits behind the same network boundary as production and the risk was
> acceptable.
>
> For completeness: `sqldb-uat` is in `sub-nonprod`. Defender for Cloud is on
> the free tier there, the landing-zone policy initiative is applied in
> audit-only mode, and I believe SQL auditing is on but not connected to
> anything. Twenty-one people hold Contributor on that subscription.
>
> Current row count in the UAT customer table is 181,402.
>
> Adeola

---

## Artefact 2 — `refresh_uat.ps1`, held on the DC-SLO host

Extract. Provided by the platform team on request.

```powershell
# refresh_uat.ps1 — nightly UAT refresh. Runs 02:00 via scheduled task.
# Owner: platform. Last modified 2024-03-11.

$prod = "Server=sqlmi-prod.xxxxx.database.windows.net;Database=finserve;User ID=svc_uatrefresh;Password=R3fr3sh-Uat-2024;Encrypt=True"   # SIM-FAKE inject-07
$uat  = "Server=sqldb-uat.database.windows.net;Database=finserve_uat;User ID=svc_uatrefresh;Password=R3fr3sh-Uat-2024;Encrypt=True"       # SIM-FAKE inject-07

Copy-SqlDatabase -Source $prod -Target $uat -Overwrite

# Masking. Names and email only - see PROD-TEST-042 for the decision.
Invoke-Sqlcmd -ConnectionString $uat -Query @"
UPDATE dbo.Customer
   SET Forename = CONCAT('Test', CustomerId),
       Surname  = CONCAT('User', CustomerId),
       Email    = CONCAT('uat', CustomerId, '@finserve-test.example');
"@

# TODO: NINO, DOB, address, balances. Blocked by recon test pack - PROD-TEST-042
```

---

## What you are asked to produce

### GRC team

**Data protection impact assessment** → `06-DELIVERABLES/GRC/UAT-Data-DPIA.md`

- What personal data is in `sqldb-uat`, by category, using D1–D7.
- Lawful basis for processing production personal data in a test environment.
  If you conclude there isn't one, say so in those words.
- Assess it against the UK GDPR principles that bite hardest here. Purpose
  limitation and data minimisation are the obvious two; decide whether
  integrity and confidentiality is a third.
- The control differential. Production and UAT hold the same data under
  different protection. Quantify the gap using the architecture, don't
  characterise it.
- Risk to data subjects if this environment were accessed by an unauthorised
  party. Reason it through rather than asserting "high".
- Recommendation, with a position on the reconciliation test pack — the
  engineering reason for this is real and "mask it anyway" is not a plan.

Add it to the risk register and say what score you are giving it and why.

### SOC team

**Impact reassessment** → extend `06-DELIVERABLES/SOC/INC-01-Invoice-Phish.md`

Revisit your scope assessment from Inject 06 in light of what this database
contains. Specifically:

- What is now the worst case for the connections observed at W2 D7 04:11?
- What evidence would confirm or exclude exfiltration, and does it exist?
- Restate what you can prove, what you assess as likely, and what you cannot
  rule out. If the third category grew, say so — it should.
- If your severity rating changes, change it, and date the change.

## Where it goes

`06-DELIVERABLES/GRC/` and `06-DELIVERABLES/SOC/` respectively.

## Time budget

Two days.

## Note

You have both received this email. You have not received each other's work.

One team is holding a compliance finding about a database. The other is holding
a firewall log showing a connection to a database. Whether those are the same
database is a question somebody has to ask out loud.

Nothing in this inject tells you to go and talk to the other team. Nothing
stops you either.
