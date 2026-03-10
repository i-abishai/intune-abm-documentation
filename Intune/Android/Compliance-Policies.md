# Android Compliance Policies

**Snapshot Date:** March 10, 2026

> 🚨 **Critical:** Google Mobile Services (GMS)-based **Device Administrator management ended December 31, 2024**. Migration to Android Enterprise is required immediately for the 4 enrolled Android devices.

## Policies

| Policy Name | Type | Last Modified |
|---|---|---|
| android_standard_compliance | Android device administrator compliance policy | 11/03/2025 |

> *Detailed compliance settings to be populated from Graph API export.*

```powershell
Get-MgDeviceManagementDeviceCompliancePolicy | Where-Object { $_.ODataType -like "*Android*" } | Format-List
```
