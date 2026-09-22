# Inject 04 — Invoice phish

**Release:** Week 2, Day 1, 08:40 · **Team:** SOC · **Deliverable due:** W2 D3

---

## Artefact 1 — the reported email

Forwarded to `phishing@finserve.co.uk` by a Finance Operations analyst at
08:31, with the note *"This doesn't look right but Nadia says she sent it?"*

```
Received: from mail-ukw1-f174.outbound.smtpsvc.example (203.0.113.87)
 by GB2PR09MB4417.eurprd09.prod.outlook.com with HTTPS; W2 D1 07:52:11 +0000
Authentication-Results: spf=fail (sender IP is 203.0.113.87)
 smtp.mailfrom=finserve.co.uk; dkim=none (message not signed)
 header.d=none; dmarc=fail action=none header.from=finserve.co.uk
From: "Nadia Ferreira" <n.ferreira@finserve.co.uk>
Reply-To: "Nadia Ferreira" <n.ferreira@finserve-co.example>
To: "Rachel Oduya" <r.oduya@finserve.co.uk>
Subject: Meridian Trust — revised settlement schedule, needs sign-off today
Date: W2 D1 07:52:09 +0000
X-Originating-IP: [203.0.113.87]
```

> Rachel,
>
> Meridian have sent through a revised settlement schedule ahead of the
> quarter close and Treasury need it acknowledged before 10:00 today. I am on
> the Manchester train with no signal to speak of so I cannot do it from here.
>
> The document is on the finance portal — you will need to sign in, it has
> the customer breakdown in it so it is restricted.
>
> https://finserve-co.example/portal/sso/auth?ref=settle-q4&rd=sharepoint
>
> Can you confirm once done. Sorry to drop this on you.
>
> Nadia
>
> Sent from my iPhone

**Notes from the service desk ticket (SD-2026-4417):**
Six recipients, all in Finance Operations. Four deleted it. One reported it at
08:31. One — `r.oduya@finserve.co.uk` — replied to the sender at 07:58 saying
"done".

---

## Artefact 2 — Sentinel incident, raised 08:47

```
Incident      : 2026-W2D1-0093
Title         : Atypical travel involving one user
Severity      : Medium
Status        : New
Analytics rule: Microsoft built-in — "Atypical travel"
Entity        : r.oduya@finserve.co.uk
First activity: W2 D1 07:59:44 UTC
```

| Time (UTC) | App | IP | Location | ASN | Result | MFA |
|---|---|---|---|---|---|---|
| 07:41:02 | Office 365 Exchange Online | 81.2.69.144 | London, GB | Corporate ExpressRoute | Success | Satisfied — claim in token |
| 07:59:44 | Office 365 Exchange Online | 45.83.220.61 | Manchester, GB | AS205544 (hosting) | Success | **Satisfied — claim in token** |
| 08:02:17 | Microsoft Graph | 45.83.220.61 | Manchester, GB | AS205544 (hosting) | Success | Satisfied — claim in token |
| 08:14:55 | Office 365 SharePoint Online | 45.83.220.61 | Manchester, GB | AS205544 (hosting) | Success | Satisfied — claim in token |
| 09:31:08 | Office 365 Exchange Online | 81.2.69.144 | London, GB | Corporate ExpressRoute | Success | Satisfied — claim in token |

Conditional Access evaluation for the 07:59:44 sign-in:

```
Policy 1 — Require MFA for all users .................. Not applied (MFA claim present in token)
Policy 3 — Block legacy authentication ................ Not applied (modern auth)
Policy 5 — Block access from outside UK/IE/ES ......... Not applied (GB)
Policy 7 — Session controls, unmanaged devices ........ Applied — app-enforced restrictions
Policy 9 — High sign-in risk, require password change . Not applied (risk = low)
```

---

## Artefact 3 — Unified Audit Log extract, `r.oduya@finserve.co.uk`

```
W2 D1 08:02:44  New-InboxRule  Name="...."  SubjectOrBodyContainsWords="meridian;settlement;reconciliation"
                               MoveToFolder="RSS Subscriptions"  MarkAsRead=True
W2 D1 08:05:19  MailItemsAccessed  Folder=Inbox  ClientAppId=Graph
W2 D1 08:09:03  MailItemsAccessed  Folder="Settlement Ops (shared)"  ClientAppId=Graph
W2 D1 08:14:55  FileAccessed   Site="/sites/FinanceOps"  File="Settlement runbook v4.docx"
W2 D1 08:16:30  FileDownloaded Site="/sites/FinanceOps"  File="Settlement runbook v4.docx"
W2 D1 08:22:41  FileAccessed   Site="/sites/FinanceOps"  File="DR-SLO access notes.txt"
W2 D1 08:23:02  FileDownloaded Site="/sites/FinanceOps"  File="DR-SLO access notes.txt"
```

The inbox rule name is a single full stop.

---

## What you are asked to produce

**SOC team.**

**1. Incident report** → `06-DELIVERABLES/SOC/INC-01-Invoice-Phish.md`

- What happened, as a timeline in UTC, stated as fact where you have evidence
  and as assessment where you do not. Mark which is which.
- How the control stack was defeated. Be precise. Six controls were in the
  path and the sign-in succeeded; explain what each one did.
- Scope. What did the attacker access, what did they take, and what can you
  *not* rule out. The last one matters most.
- Severity and your justification.

**2. Containment and eradication actions** → same document

What you would do, in what order, in the next hour. Distinguish actions that
stop the bleeding from actions that preserve evidence, and say where the two
conflict.

**3. Detection gap** → append to `06-DELIVERABLES/SOC/Detection-Backlog.md`

This incident was detected by a built-in rule 47 minutes after the first
malicious sign-in, and the detection it fired on is not the one that mattered.
What would have caught it sooner? Write the detection.

## Where it goes

`06-DELIVERABLES/SOC/`, PR from `soc/<initials>/inc-01`.

## Time budget

Two days.

## Note

You have three artefacts and no access to a live tenant. Where you would
normally run a query, say what query you would run and what you would expect it
to return. An analyst who writes "I would check X" and is specific about X is
demonstrating more than one who asserts a conclusion the evidence does not
carry.

Two of the downloaded files are named in the audit log. Think about what the
attacker now knows that they did not know at 07:52.
