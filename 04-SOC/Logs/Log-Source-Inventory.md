# FinServe — Log Source Inventory

**Owner:** Security Operations Manager · **Workspace:** `law-sentinel-prod`
**Subscription:** `sub-management` · **As at:** September 2025

> Compiled by the infrastructure team during Project Lighthouse and updated by
> Security Operations on request. This records what is *believed* to be
> collected. It has not been reconciled against the estate.

---

## 1. Sentinel data connectors

| Connector | Status | Tables | Retention |
|---|---|---|---|
| Azure Activity | Connected | `AzureActivity` | 60 days |
| Entra ID — sign-in logs | Connected | `SigninLogs`, `AADNonInteractiveUserSignInLogs` | 60 days |
| Entra ID — audit logs | Connected | `AuditLogs` | 60 days |
| Microsoft 365 | Connected | `OfficeActivity` | 60 days |
| Microsoft Defender XDR | Connected | `SecurityAlert`, `SecurityIncident` | 60 days |
| Defender for Cloud | Connected | `SecurityAlert` | 60 days |
| Azure Firewall | Connected via diagnostic settings | `AZFWApplicationRule`, `AZFWNetworkRule` | 60 days |
| Azure WAF / Front Door | Connected via diagnostic settings | `AzureDiagnostics` | 60 days |
| Threat Intelligence — Microsoft | Connected | `ThreatIntelligenceIndicator` | 60 days |
| Windows Security Events via AMA | Connected — 4 hosts | `SecurityEvent` | 60 days |
| Syslog via AMA | Connected — 2 hosts | `Syslog` | 60 days |
| **Azure SQL — auditing** | **Not connected** | — | — |
| **Azure Storage — diagnostics** | **Not connected** | — | — |
| **AKS — audit log** | **Not connected** | — | — |
| Corebridge | Not available | — | — |

## 2. Hosts forwarding to the workspace

### Windows Security Events (AMA) — 4 hosts

| Host | Role | Data collection rule |
|---|---|---|
| `DC-01` | Domain controller | `dcr-security-events-common` |
| `DC-02` | Domain controller | `dcr-security-events-common` |
| `JUMP-01` | Administrative jump host | `dcr-security-events-common` |
| `ENTRACONNECT-01` | Entra Connect server | `dcr-security-events-common` |

The data collection rule is set to the **Common** event set, not All.

### Syslog (AMA) — 2 hosts

| Host | Role | Facilities |
|---|---|---|
| `FGT-HQ-01` | Fortigate pair, HQ | local0, auth, authpriv |
| `FGT-SLO-01` | Fortigate pair, DC-SLO | local0, auth, authpriv |

## 3. Systems in the estate with no telemetry reaching the workspace

Compiled by Security Operations in September 2025 at the CISO's request. Not
formally reviewed.

| System | Logs locally? | Local retention | Notes |
|---|---|---|---|
| Branch firewall — Manchester | Yes | 14 days on device | No forwarder configured |
| Branch firewall — Birmingham | Yes | 14 days on device | No forwarder configured |
| Branch firewall — Leeds | Yes | 14 days on device | No forwarder configured |
| DC-SLO SFTP server | Yes | 30 days on device | `auth.log`, `sftp-server` facility. No forwarder |
| DC-SLO backup appliance | Yes | 90 days on device | Vendor appliance, syslog possible, not configured |
| FinRecon application host | Application log only | Unknown | No security logging |
| Branch counter systems | Yes | Unknown | Kestrel-era, no documentation |
| Contact centre telephony | Vendor-held | Per contract | Access by ticket |
| Azure SQL Managed Instance | **Auditing enabled** | 1 year in storage account | Audit writes to storage; **no Sentinel connector** |
| Azure Storage accounts | Diagnostics off | — | — |
| AKS clusters | Container logs only | 30 days | Control-plane audit log not enabled |
| Corebridge | Vendor-held | Per contract | Access by ticket, typically 5 working days |

## 4. Retention

Workspace retention is **60 days** across all tables. Archive tier is not
configured. There is no long-term retention to storage for any table except
the Azure SQL audit, which writes to an immutable storage account with a
one-year policy and is not queryable from Sentinel.

An extension to 365 days was priced at approximately £31,000 per year during
the FY2026 budget round and was not approved.

## 5. Known limitations

Recorded by Security Operations:

- The inventory has never been reconciled against the asset register
- No verification that a connected source is *still* sending — there is no
  ingestion-gap monitoring and no alert on a source going silent
- The `SecurityEvent` collection rule uses the Common event set; several event
  IDs relevant to credential access are outside it
- Ingestion volume is not monitored against cost, so an unexpected drop would
  not be noticed financially either
