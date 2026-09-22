# FinServe — Security Incident Log

**Owner:** Security Operations · **Covers:** January 2024 to W1 D1
**Source:** service desk, filtered to the Security category

---

## 1. Recorded incidents

| Ref | Date | Summary | Severity | Closed | Days open |
|---|---|---|---|---|---|
| SEC-2024-01 | 2024-03-11 | Phishing wave, 61 recipients, credential harvesting page | Medium | 2024-03-14 | 3 |
| SEC-2024-02 | 2024-04-02 | Laptop lost on public transport, encrypted, wiped remotely | Low | 2024-04-03 | 1 |
| SEC-2024-03 | 2024-05-19 | Defender detection — commodity malware on a contractor device | Low | 2024-05-19 | 0 |
| SEC-2024-04 | 2024-06-27 | Business email compromise attempt against Finance, not successful | Medium | 2024-07-04 | 7 |
| SEC-2024-05 | 2024-08-14 | Reported email, credential harvesting, 4 recipients | Low | 2024-08-15 | 1 |
| SEC-2024-06 | 2024-09-30 | Malware detection on a corporate laptop, contained by Defender | Low | 2024-09-30 | 0 |
| SEC-2024-07 | 2024-11-08 | Failed RDP attempts against JUMP-01 from an external address | Medium | 2024-11-12 | 4 |
| SEC-2025-01 | 2025-02-06 | Reported email, payslip-themed phishing, 12 recipients | Low | 2025-02-07 | 1 |
| SEC-2025-02 | 2025-03-19 | Tor sign-in attempt against a privileged account, blocked | Medium | 2025-03-21 | 2 |
| SEC-2025-03 | 2025-06-11 | Reported email, invoice-themed, 8 recipients, 1 click | Medium | 2025-06-18 | 7 |
| SEC-2025-04 | 2025-07-23 | Third-party consent grant to an unapproved application | Low | 2025-07-24 | 1 |
| SEC-2025-05 | 2025-09-02 | Defender detection — potentially unwanted application | Low | 2025-09-02 | 0 |

**12 recorded security incidents in 21 months.**

## 2. Not recorded here

The three customer-facing outages in Q1 2025 that prompted the FCA information
request were handled as **major incidents** by the Technology function under
the Incident Management Policy, not as security incidents, and are not in this
log. Security Operations was not engaged on any of the three.

## 3. Post-incident review

The Incident Management Policy requires a post-incident review for any
incident rated Medium or above.

| Incident | Severity | PIR held | Actions raised | Actions closed |
|---|---|---|---|---|
| SEC-2024-01 | Medium | Yes | 3 | 3 |
| SEC-2024-04 | Medium | Yes | 2 | 1 |
| SEC-2024-07 | Medium | No | — | — |
| SEC-2025-02 | Medium | No | — | — |
| SEC-2025-03 | Medium | Yes | 4 | 1 |

Three of five eligible incidents had a review. Of nine actions raised, five
remain open. The oldest, from SEC-2024-04, is *"Review the payment
authorisation process for out-of-band verification"* — owner Head of Finance
Operations, raised July 2024.

## 4. SEC-2025-03 — worth reading

June 2025. An invoice-themed phishing email reached eight recipients in
Finance. One clicked and entered credentials on a harvesting page. The account
was reset within four hours and no unauthorised access was identified.

The post-incident review raised four actions:

1. Extend anti-phishing impersonation protection beyond the executive list —
   **open**
2. Implement DMARC enforcement (`p=quarantine` then `p=reject`) —
   **open**, owner Head of Digital Workplace
3. Targeted awareness training for Finance Operations — **closed**, delivered
   September 2025
4. Review whether session tokens are revoked on password reset — **open**

Action 4 was raised because the analyst handling the incident was unsure
whether resetting the password terminated the attacker's session. The question
was recorded and not answered.

## 5. Metrics

| | 2024 | 2025 to date |
|---|---|---|
| Incidents recorded | 7 | 5 |
| Medium or above | 3 | 2 |
| Post-incident reviews held | 2 of 3 | 1 of 2 |
| Mean time to close | 2.3 days | 2.2 days |
| Incidents identified by a detection rule | 2 | 1 |
| Incidents identified by a user report | 5 | 4 |

Eight of twelve incidents were identified because a person reported them.
