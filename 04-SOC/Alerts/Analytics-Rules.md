# FinServe — Sentinel Analytics Rules

**Workspace:** `law-sentinel-prod` · **As at:** September 2025
**Maintained by:** Security Operations

---

## 1. Microsoft built-in templates — enabled as shipped

Enabled during Project Lighthouse by the deployment partner. None has been
tuned, and no exclusions have been added.

| Rule | Source | Severity | Status |
|---|---|---|---|
| Atypical travel | `SigninLogs` | Medium | Enabled |
| Sign-ins from IPs that attempt sign-ins to disabled accounts | `SigninLogs` | Medium | Enabled |
| Brute force attack against user credentials | `SigninLogs` | Medium | Enabled |
| Sign-in from an anonymous IP address | `SigninLogs` | Medium | Enabled |
| Sign-in from an unfamiliar location | `SigninLogs` | Medium | Enabled |
| Suspicious application consent | `AuditLogs` | Medium | Enabled |
| User added to privileged group | `AuditLogs` | Medium | Enabled |
| Azure Firewall — high volume of blocked traffic | `AZFWNetworkRule` | Low | Enabled |
| Azure Activity — suspicious resource deployment | `AzureActivity` | Low | Enabled |
| Azure Activity — NSG rule modified | `AzureActivity` | Low | Enabled |
| Azure Activity — Key Vault policy changed | `AzureActivity` | Medium | Enabled |
| Azure Activity — diagnostic settings deleted | `AzureActivity` | Medium | Enabled |

**12 built-in rules enabled.** The Microsoft template gallery offers
considerably more for the connectors in use; no assessment has been made of
which of the remainder are applicable.

## 2. Custom rules

Four. Written by the deployment partner in 2024. No design notes were handed
over.

---

### CUST-01 — Failed sign-in burst

**Frequency:** every 1 hour · **Lookback:** 1 hour · **Severity:** Medium
**Author:** deployment partner, 2024-06

```kql
SigninLogs
| where TimeGenerated > ago(1h)
| where ResultType != 0
| summarize FailedCount = count() by UserPrincipalName, IPAddress, bin(TimeGenerated, 10m)
| where FailedCount > 10
| project TimeGenerated, UserPrincipalName, IPAddress, FailedCount
```

**Ops note (Marcus Ifill):** "Fires constantly. Mostly people with an old
password cached on a phone. It is the single biggest contributor to the queue."

---

### CUST-02 — Privileged role assignment outside change window

**Frequency:** every 1 hour · **Lookback:** 1 hour · **Severity:** High
**Author:** deployment partner, 2024-07

```kql
AuditLogs
| where OperationName == "Add member to role"
| where Result == "success"
| extend RoleName = tostring(TargetResources[0].modifiedProperties[1].newValue)
| extend Actor = tostring(InitiatedBy.user.userPrincipalName)
| where TimeGenerated between (startofday(TimeGenerated) + 9h .. startofday(TimeGenerated) + 17h)
| project TimeGenerated, Actor, RoleName
```

**Ops note (Marcus Ifill):** "One of the two I cannot explain. It is called
'outside change window' and I am fairly sure the change window is 09:00 to
17:00, but I have not sat down with it. It does fire. I have never had one that
turned out to be anything."

---

### CUST-03 — Database mass export

**Frequency:** every 1 hour · **Lookback:** 1 hour · **Severity:** High
**Author:** deployment partner, 2024-07

```kql
SQLSecurityAuditEvents
| where TimeGenerated > ago(1h)
| where Statement has_any ("SELECT *", "BULK", "bcp", "OPENROWSET")
| summarize RowsAffected = sum(AffectedRows) by ServerName, DatabaseName, ClientIp, ApplicationName
| where RowsAffected > 10000
| project ServerName, DatabaseName, ClientIp, ApplicationName, RowsAffected
```

**Ops note (Marcus Ifill):** "The other one I cannot explain. It has never
fired. I took that as good news for a long time."

---

### CUST-04 — Multiple sign-in locations in a day

**Frequency:** every 12 hours · **Lookback:** 1 day · **Severity:** Medium
**Author:** deployment partner, 2024-06

```kql
SigninLogs
| where ResultType == 0
| extend Country = tostring(LocationDetails.countryOrRegion)
| summarize Countries = make_set(Country), CountryCount = dcount(Country)
    by UserPrincipalName, bin(TimeGenerated, 1d)
| where CountryCount > 1
| project TimeGenerated, UserPrincipalName, Countries, CountryCount
```

**Ops note (Marcus Ifill):** "Anyone who turns a VPN on. Anyone on holiday who
checks their email. We get a handful a day and they are all nothing."

---

## 3. Automation

No playbooks are configured. No automation rules are configured. Alerts are
triaged manually in the Sentinel portal.

Incident assignment is manual. There is no rule assigning incidents to an
owner, so an incident sits unassigned until someone opens the queue.

## 4. Suppression and tuning

No suppression rules. No allowlists. No watchlists.

Tuning has not been performed on any rule since deployment. The deployment
partner's handover document lists "tuning and optimisation" as a
recommended follow-on engagement, quoted at £18,000, which was not taken up.

## 5. Coverage assessment

None has been performed. The MITRE ATT&CK coverage view in Sentinel has not
been reviewed, and no mapping exists between the enabled rules and any threat
model, including the one in
[`../Threat-Intel/Threat-Profile-2025.md`](../Threat-Intel/Threat-Profile-2025.md).
