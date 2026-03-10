# Windows Compliance Policies

**Snapshot Date:** March 10, 2026

> ⚠️ Compliance policies are assigned but **Entra Conditional Access for compliance enforcement is NOT configured**. Threat Defense connectors are active for Windows.

## Policies

| Policy Name | Platform | Type | Last Modified |
|---|---|---|---|
| AO - Windows Compliance | Windows 10 and later | Windows 10/11 compliance policy | 03/01/2024 |

## AO - Windows Compliance — Settings

> *Detailed settings to be populated from Graph API export. Use the PowerShell command below to extract.*

```powershell
Get-MgDeviceManagementDeviceCompliancePolicy | Where-Object { $_.DisplayName -like "*Windows*" } | Format-List
```
