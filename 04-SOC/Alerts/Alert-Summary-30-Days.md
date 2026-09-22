# FinServe — Alert Summary, Last 30 Days

**Period:** rolling 30 days to W1 D1 · **Source:** Sentinel incident queue
**Compiled by:** Security Operations Manager

---

## 1. Headline

| | Count | % |
|---|---|---|
| Incidents raised | **847** | 100% |
| Closed — benign positive | 661 | 78.0% |
| Closed — false positive | 151 | 17.8% |
| Closed — informational | 31 | 3.7% |
| Investigated and documented | **4** | 0.5% |
| Still open at period end | 0 | — |

Median time to first touch: **5h 51m**. Longest time to first touch: 61 hours
(raised Friday 18:40, opened Monday 08:12).

## 2. By rule

| Rule | Incidents | Benign | False positive | Informational | Investigated |
|---|---|---|---|---|---|
| CUST-01 Failed sign-in burst | 391 | 358 | 33 | 0 | 0 |
| CUST-04 Multiple sign-in locations | 148 | 141 | 7 | 0 | 0 |
| Brute force attack against user credentials | 97 | 71 | 26 | 0 | 0 |
| Atypical travel | 71 | 44 | 24 | 2 | 1 |
| Sign-in from an unfamiliar location | 54 | 39 | 15 | 0 | 0 |
| Azure Firewall — high volume of blocked traffic | 31 | 0 | 31 | 0 | 0 |
| Sign-in from an anonymous IP address | 19 | 6 | 11 | 1 | 1 |
| Azure Activity — NSG rule modified | 12 | 0 | 0 | 12 | 0 |
| CUST-02 Privileged role assignment outside change window | 9 | 0 | 0 | 9 | 0 |
| User added to privileged group | 7 | 1 | 0 | 5 | 1 |
| Suspicious application consent | 4 | 1 | 2 | 0 | 1 |
| Azure Activity — Key Vault policy changed | 2 | 0 | 0 | 2 | 0 |
| Sign-ins from IPs that attempt sign-ins to disabled accounts | 2 | 0 | 2 | 0 | 0 |
| Azure Activity — suspicious resource deployment | 0 | — | — | — | — |
| Azure Activity — diagnostic settings deleted | 0 | — | — | — | — |
| **CUST-03 Database mass export** | **0** | — | — | — | — |
| **Total** | **847** | **661** | **151** | **31** | **4** |

## 3. The four investigated

| Ref | Rule | Summary | Outcome |
|---|---|---|---|
| INC-2025-0912-004 | Atypical travel | Sign-in from Spain for a user on leave | Confirmed benign. User was in Spain |
| INC-2025-0918-011 | Anonymous IP | Tor exit node sign-in attempt, failed | Blocked by Conditional Access policy 5. No action |
| INC-2025-0924-002 | User added to privileged group | Contributor granted on `sub-nonprod` outside a change | Approved retrospectively by the Cloud Platform Lead |
| INC-2025-1002-007 | Suspicious application consent | User consented to a third-party productivity add-in | Consent revoked. Tenant consent policy unchanged |

## 4. Working pattern

| | |
|---|---|
| Analysts covering the queue | 2 |
| Working hours | 09:00–17:30, Mon–Fri |
| Out-of-hours | No rota. Alerts page the Security Operations Manager's mobile |
| Incidents raised outside working hours | 214 (25.3%) |
| Median time to first touch, out-of-hours incidents | 14h 22m |

## 5. Notes from the Security Operations Manager

> Two rules produce 64% of the queue. I know that and I have not turned them
> off, because turning off a noisy rule and turning off a rule are the same
> action and I would rather have the noise than explain why I disabled
> detection.
>
> "Benign positive" in our queue mostly means "the activity happened and it was
> fine". "False positive" means "the rule was wrong". I am not confident every
> analyst has applied that distinction consistently, mine included.
>
> Four investigations in thirty days is not four interesting things happening.
> It is four things that survived triage.
