# macOS Compliance Policies

**Snapshot Date:** March 10, 2026

> ⚠️ Compliance policies are assigned but **Entra Conditional Access for compliance enforcement is NOT configured**.

## Policies

| Policy Name | Type | Last Modified |
|---|---|---|
| RapsodoMacOsPolicy | Mac compliance policy | 08/10/2022 |
| AO - MacOS Compliance | Mac compliance policy | 01/23/2024 |

> *Detailed compliance settings to be populated from Graph API export.*

```powershell
Get-MgDeviceManagementDeviceCompliancePolicy | Where-Object { $_.ODataType -like "*macOS*" } | Format-List
```
