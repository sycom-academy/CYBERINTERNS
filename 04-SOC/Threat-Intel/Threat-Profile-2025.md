# FinServe — Threat Profile 2025

**Prepared by:** Security Operations · **Approved by:** CISO
**Date:** February 2025 · **Review:** annual

Prepared to support the annual information security risk assessment and the
Risk Committee paper of March 2025.

---

## 1. Sector threat landscape

UK retail banking faces a threat landscape dominated by financially motivated
cybercrime. The principal categories are:

**Ransomware.** Groups operating ransomware-as-a-service continue to target
financial services. Initial access is typically obtained through phishing,
exposed remote access services, or exploitation of internet-facing
vulnerabilities. Double extortion — encryption plus data theft — is now
standard.

**Business email compromise and payment fraud.** Attackers compromise or
impersonate a mailbox to redirect payments or authorise fraudulent
transactions. Finance functions are the primary target.

**Credential phishing.** High volume, low sophistication at the commodity end;
adversary-in-the-middle proxy kits capable of capturing session tokens at the
more capable end. The latter defeat multi-factor authentication where the
factor is satisfied at sign-in rather than continuously evaluated.

**Third-party and supply chain compromise.** Attackers target service
providers to reach their customers. Financial services firms typically have
extensive provider estates.

**Insider risk.** Malicious and negligent. Under-reported across the sector.

**Denial of service.** Hacktivist-motivated DDoS against UK financial
institutions has been observed periodically.

## 2. Threat actors of relevance

| Category | Motivation | Relevance to FinServe |
|---|---|---|
| Ransomware affiliates | Financial | High — sector targeted, estate includes legacy on-premises |
| BEC / payment fraud operators | Financial | High — finance function processes settlement |
| Commodity phishing | Financial | High — volume |
| Hacktivists | Ideological | Low — no current political profile |
| Nation-state | Espionage | Low — FinServe is not a systemically important institution |

## 3. Attack surface

- Internet-facing: mobile application, internet banking web front end, public
  website, VPN gateway
- Email: 470 mailboxes
- Remote access: point-to-site VPN, administrative jump host
- Third parties with connectivity or data access: see the supplier register
- Staff: 450, of whom approximately 120 work remotely at any time

## 4. Assessment

The principal threats to FinServe are assessed as ransomware affecting the
corporate estate, and business email compromise targeting the finance
function.

These are reflected in the risk register as R-09 and, in part, R-13.

## 5. Controls relied upon

| Threat | Primary controls |
|---|---|
| Ransomware | Defender for Endpoint, email filtering, backups, awareness training |
| BEC | Multi-factor authentication, external sender banner, payment authorisation process |
| Credential phishing | Multi-factor authentication, Conditional Access, Safe Links |
| Third party | Due diligence at onboarding, contractual provisions |
| DDoS | Azure Front Door, Cloudflare |

## 6. Gaps identified

None recorded in this assessment.

---

## Document notes

Sections 1 and 2 are adapted from the 2024 threat landscape publications of two
vendors and the NCSC annual review. Sections 3 to 5 were completed by Security
Operations.

No mapping has been made between the threats identified here and the analytics
rules in
[`../Alerts/Analytics-Rules.md`](../Alerts/Analytics-Rules.md). The
assessment was not used to prioritise detection development, and no detection
work followed from it.

This document has not been revised since February 2025.
