# Intune Tenant Overview

**Snapshot Date:** March 10, 2026

## Device Inventory

| Platform | Total Devices |
|---|---|
| Windows | 151 |
| macOS | 66 |
| iOS/iPadOS | 0 |
| Android | 4 |
| Linux | 0 |
| **Total Managed** | **221** |

## Autopatch & Update Status

| Metric | Value |
|---|---|
| Devices managed by cloud policies | 143 |
| Assigned to update rings | 143 |
| Profiles with error or conflict | 12 |
| Noncompliant devices | 65 |
| Devices not evaluated | 7 |

> ⚠️ **Compliance Rate:** ~70% (65 of 221 devices noncompliant)

## Policy Summary

| Category | Count |
|---|---|
| Configuration Policies | 87 |
| Compliance Policies | 6 |
| Remediation Script Packages | 6 |
| Platform Scripts | 17 |
| Windows Update Rings | 3 |

## Active Windows Update Deployments

| Release | Type | Status | First Deployment |
|---|---|---|---|
| 2026.03 B | Quality Update | In Progress | 3/10/2026 |
| Windows 11 25H2 | Feature Update | In Progress | 12/23/2025 |

## Key Observations

1. **⚠️ Conditional Access not configured** — Compliance policies are assigned but Entra CA for compliance enforcement is NOT active.
2. **⚠️ 12 profiles have assignment errors/conflicts** — requires investigation.
3. **⚠️ 65 noncompliant devices** out of 221 total (~70% compliance rate).
4. **✅ Defender for Endpoint connector is enabled** — EDR active on Windows and macOS.
5. **⚠️ iOS/iPadOS: 0 enrolled devices** — compliance policies exist but no enrolled devices.
6. **🚨 Android GMS device administrator management ended Dec 31, 2024** — migration to Android Enterprise required.
7. **🚨 Windows 10 End of Support: October 14, 2025** — Feature update to Windows 11 25H2 is In Progress.
8. **✅ Extensive ASR coverage** — both Block and Audit modes across all devices.
