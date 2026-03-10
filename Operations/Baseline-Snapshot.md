# Baseline Snapshot Report

**Generated:** March 10, 2026  
**Purpose:** Configuration drift reference — compare future states against this baseline.

---

## Tenant Statistics

| Metric | Value |
|---|---|
| Total Managed Devices | 221 |
| Windows | 151 |
| macOS | 66 |
| iOS/iPadOS | 0 |
| Android | 4 |
| Configuration Policies | 87 |
| Compliance Policies | 6 |
| Remediation Script Packages | 6 |
| Platform Scripts | 17 |
| Update Rings | 3 |
| Autopatch-managed Devices | 143 |
| Noncompliant Devices | 65 |
| Profiles with Error/Conflict | 12 |

---

## ⚠️ Open Action Items

| # | Severity | Issue | Recommendation |
|---|---|---|---|
| 1 | 🔴 Critical | Entra Conditional Access not configured for compliance | Configure CA policies to block/limit access for noncompliant devices |
| 2 | 🔴 Critical | Android Device Administrator management deprecated (Dec 31, 2024) | Migrate 4 Android devices to Android Enterprise immediately |
| 3 | 🟡 High | Windows 10 End of Support passed (Oct 14, 2025) | Ensure all Windows 10 devices are upgraded to Windows 11 25H2 |
| 4 | 🟡 High | 65 noncompliant devices (70% compliance rate) | Investigate and remediate noncompliant device list |
| 5 | 🟡 High | 12 profiles with assignment errors/conflicts | Audit profile assignments; resolve BitLocker PIN conflict (200 conflicts) |
| 6 | 🟡 High | FileVault policy — 3 device errors | Check macOS version compatibility and enrollment state |
| 7 | 🟠 Medium | iOS/iPadOS: 0 enrolled devices, policies exist | Decide on iOS enrollment strategy or deprecate unused iOS policies |
| 8 | 🟠 Medium | AM_SG_Corporate_WiFi — 67 errors | Investigate authentication/PSK mismatch for Singapore Wi-Fi |
| 9 | 🟠 Medium | Ahmet-Detection-ASR remediation: 111 devices with issues | Review ASR detection script logic |
| 10 | 🟢 Low | Multiple policies marked passive/unassigned | Review and activate or remove: WIN - Firewall Hardening v1, WIN - Account Protection Hardening, AO - Exploit Protection & Endpoint Hardening |

---

## Policy Coverage Matrix

| Policy Area | Windows | macOS | iOS | Android |
|---|---|---|---|---|
| Antivirus | ✅ | ✅ | ❌ | ❌ |
| Disk Encryption | ✅ BitLocker | ✅ FileVault | ❌ | ❌ |
| Firewall | ✅ | ✅ | ❌ | ❌ |
| EDR | ✅ | ✅ | ❌ | ❌ |
| ASR Rules | ✅ | ❌ | ❌ | ❌ |
| Compliance | ✅ | ✅ | ✅ | ✅ |
| Update Management | ✅ Autopatch | ✅ DDM | ❌ | ❌ |
| Account Protection / WHfB | ✅ | ❌ | ❌ | ❌ |
| App Control (AppLocker) | ✅ | ❌ | ❌ | ❌ |

---

## Drift Detection — How to Use This Baseline

To detect configuration drift, re-run the following export and compare against this snapshot:

```powershell
# Export all configuration policies
Get-MgDeviceManagementDeviceConfiguration | Select-Object DisplayName, LastModifiedDateTime | Export-Csv -Path .\drift-check-$(Get-Date -Format yyyyMMdd).csv -NoTypeInformation

# Export compliance policies
Get-MgDeviceManagementDeviceCompliancePolicy | Select-Object DisplayName, LastModifiedDateTime | Export-Csv -Path .\compliance-drift-$(Get-Date -Format yyyyMMdd).csv -NoTypeInformation
```

Compare output against this baseline snapshot to identify:
- New policies added
- Existing policies modified (LastModifiedDateTime change)
- Policies removed
