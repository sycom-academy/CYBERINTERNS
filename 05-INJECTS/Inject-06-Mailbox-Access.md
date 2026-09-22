# Inject 06 — What the runbook was for

**Release:** Week 3, Day 1, 07:15 · **Team:** SOC · **Deliverable due:** W3 D3

---

## Artefact 1 — inbound, 07:12

> **From:** Operations Risk, Meridian Trust plc
> **To:** settlement.ops@finserve.co.uk
> **Cc:** p.raman@finserve.co.uk
> **Date:** W3 D1, 07:12
> **Subject:** URGENT — unexpected authentication activity, finserve_settle
>
> Colleagues,
>
> Our SFTP platform logged eleven authentications against the
> `finserve_settle` account over the weekend from an address we do not hold
> on your allowlist. Nine were successful. They occurred outside your
> contracted delivery window of 00:00–01:00.
>
> The account was used to **list** and **retrieve** directory contents. Your
> contracted use of this account is write-only delivery. Retrieval is not
> something your integration does.
>
> Source address: 45.83.220.61
>
> We have suspended the account pending your response. Tonight's settlement
> will not deliver. Please treat as urgent and confirm whether this activity
> is authorised.
>
> Operations Risk
> Meridian Trust plc

---

## Artefact 2 — DC-SLO SFTP server, local syslog

Retrieved by hand from the host. This server is not onboarded to Sentinel;
local retention is 30 days.

```
W2 D6 22:04:11 sftp-slo sshd[21884]: Accepted password for finserve_settle from 45.83.220.61 port 51122
W2 D6 22:04:19 sftp-slo sftp-server[21890]: opendir "/settlement/outbound"
W2 D6 22:04:20 sftp-slo sftp-server[21890]: opendir "/settlement/archive"
W2 D6 22:06:52 sftp-slo sftp-server[21890]: open "/settlement/archive/SETL-2026W2D5.csv" flags READ
W2 D6 22:07:31 sftp-slo sftp-server[21890]: open "/settlement/archive/SETL-2026W2D4.csv" flags READ
W2 D6 22:19:07 sftp-slo sshd[21884]: Received disconnect from 45.83.220.61
W2 D7 03:51:44 sftp-slo sshd[24011]: Accepted password for finserve_settle from 45.83.220.61 port 44518
W2 D7 03:52:02 sftp-slo sftp-server[24017]: opendir "/opt/finrecon/conf"
W2 D7 03:52:40 sftp-slo sftp-server[24017]: open "/opt/finrecon/conf/deliver.cfg" flags READ
W2 D7 03:53:18 sftp-slo sftp-server[24017]: open "/opt/finrecon/conf/refresh_uat.ps1" flags READ
W2 D7 04:02:55 sftp-slo sshd[24011]: Received disconnect from 45.83.220.61
```

Nine further successful authentications between W2 D6 and W3 D1 follow the same
pattern. The host's `auth.log` begins on W-2 D1 — entries before that have
rotated out.

---

## Artefact 3 — Azure Firewall, `law-sentinel-prod`

```
| TimeGenerated       | SourceIp      | DestinationIp | DestinationPort | Action | Rule
| W2 D7 04:11:09      | 172.20.14.30  | 10.30.2.14    | 1433            | Allow  | CHG-2025-0132-dev-fileshare
| W2 D7 04:11:12      | 172.20.14.30  | 10.30.2.14    | 1433            | Allow  | CHG-2025-0132-dev-fileshare
| W2 D7 04:14:38      | 172.20.14.30  | 10.30.2.14    | 1433            | Allow  | CHG-2025-0132-dev-fileshare
```

`172.20.14.30` is the DC-SLO SFTP server. `10.30.2.14` is `sqldb-uat` in
`sub-nonprod`.

Query for the corresponding SQL-side activity returns:

```
SQLSecurityAuditEvents
| where TimeGenerated between (datetime(W2 D7 00:00) .. datetime(W2 D7 23:59))
| where _ResourceId contains "sqldb-uat"

No results.
```

---

## Artefact 4 — Marcus, 07:31

> The SQL audit connector. I raised it twice. Twice.
>
> I can tell you a connection happened because the firewall saw it. I cannot
> tell you what it did, what it ran, or what came back. Storage diagnostics
> are off too so if anything went out to a blob I cannot see that either.
>
> The SFTP box logs locally for 30 days and nothing forwards. The auth log
> starts two weeks before the first entry you have got. I do not know whether
> this started at the weekend or has been going on since February.
>
> What do you need from me.

---

## What you are asked to produce

**SOC team.**

**1. Updated incident report** → extend `06-DELIVERABLES/SOC/INC-01-Invoice-Phish.md`

This is the same incident. Do not open a second one — merge it, and say in the
document why you assess them as linked. If you do not assess them as linked,
say that and defend it.

- **Revised timeline.** W2 D1 through W3 D1, UTC, evidence-backed.
- **The path.** How the actor got from a stolen session token to an
  authenticated session on a server in Slough. Name each step and the artefact
  that evidences it. Where you are inferring, say so.
- **What you cannot establish, and why.** Be exact about which questions are
  unanswerable, which log source would have answered them, and whether the
  data never existed or has aged out. Those are different failures with
  different fixes.
- **Earliest possible compromise.** Not the earliest you can see. The earliest
  you cannot rule out. Justify the difference.

**2. Containment plan** → same document

The settlement account is suspended and tonight's file will not deliver. That
is a live business impact. Recommend what to do about the account, the host,
and the credential — and say what you need to preserve before anyone rebuilds
anything.

**3. Answer Marcus** → `06-DELIVERABLES/SOC/INC-01-Evidence-Requests.md`

He asked what you need. Write the list: system, artefact, why you need it, and
what you will conclude from it either way. A request you cannot justify is one
you should not make.

## Where it goes

`06-DELIVERABLES/SOC/`, PR from `soc/<initials>/inc-01-escalation`.

## Time budget

Two days, and the clock in the scenario is running.

## Note

Two files were read from `/opt/finrecon/conf` at 03:52 on W2 D7. Nineteen
minutes later the same host opened a connection you can see the shape of and
not the content. Read the filenames.

The GRC team receives something tomorrow morning. You are not told what. If you
think they need something you have, that is your call to make, not your
mentor's.
