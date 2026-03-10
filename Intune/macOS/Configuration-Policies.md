# macOS Configuration Policies

**Snapshot Date:** March 10, 2026

---

## 1. Wi-Fi Profile

| Policy Name | SSID | Security | Assignment | Status |
|---|---|---|---|---|
| AM_SG_Corporate_WiFi_macOS | [CORP-SSID-SG] | WPA/WPA2-Personal | AO_device_win_test | 0 Succeeded |

**Settings:**
- Deployment Channel: Device Channel
- Connect automatically: Enable
- Hidden network: Disable
- Pre-shared key: *(masked)*

---

## 2. Endpoint Protection

| Policy Name | Assignment | Status | Last Modified |
|---|---|---|---|
| AO - Enable Gatekeeper to block apps installation | All Users (Excl: s_mdm_mac_localAdmin) | 0 Succeeded | 11/5/2024 |
| AO - MacOS firewall policy | s_mdm_macTest_tr | 0 Succeeded | — |

**Gatekeeper Settings:**
- Allow apps downloaded from: Mac App Store only

**macOS Firewall Settings:**
- Enable Firewall: True
- Enable Stealth Mode: True

---

## 3. Defender Antivirus

| Policy Name | Assignment | Status | Last Modified |
|---|---|---|---|
| MAC - Audit - PUA policy - v1 | All devices | 65 Succeeded | 12/22/2025 |

**Settings:**
- Threat type: `potentially_unwanted_application`
- Action: **Audit**

---

## 4. Settings Catalog

| Policy Name | Description | Assignment | Status | Last Modified |
|---|---|---|---|---|
| TR - macOS Enforce Latest version | Force macOS update to latest version | s_mdm_macUsers, s_mdm_macUsers_sg, s_mdm_macUsers_tr, s_mdm_macUsers_us | 52 Succeeded | 12/17/2025 |
| AM: Allow Identified Developer | Controls Gatekeeper identified developer setting | s_apps_marketing | 4 Succeeded | 9/29/2025 |
| AO - EDR Allowed System Extensions | Allows Defender system extensions | All devices | 66 Succeeded | 3/5/2025 |
| AO - FileVault policy | Full disk encryption with FileVault | All devices | 63 Succeeded, 3 Error | 2/3/2025 |
| AO - Zoom enable autoupdate (macOS) | Zoom auto-update preference | — | — | 11/1/2023 |

### TR - macOS Enforce Latest Version — Settings (DDM)

| Setting | Value |
|---|---|
| Enforce Latest Software Update Version | True |
| Delay In Days | 1 |
| Install Time | 12:00 |
| Allow Standard User OS Updates | Allowed |
| Automatic Download | Allowed |
| Automatic Install OS Updates | Allowed |
| Automatic Install Security Updates | Allowed |
| Major Deferral (days) | 1 |
| Minor Deferral (days) | 1 |
| Notifications | Enabled |

### AO - EDR Allowed System Extensions

- Team Identifier: `UBF8T346G9`
- Allowed Extensions: `com.microsoft.wdav.epsext`, `com.microsoft.wdav.netext`

### AO - FileVault Policy

- Enable: **On**
- Force Enable In Setup Assistant: True
- Prevent FileVault From Being Disabled: True
- **Status:** 3 devices with error — requires investigation.

### AM: Allow Identified Developer

- Allow Identified Developers: **False** *(more restrictive than default)*

---

## 5. EDR Custom Profiles (macOS)

All 8 EDR profiles are assigned to **All Devices** and use custom XML plist configuration profiles.

| Policy Name | Profile Name | Bundle ID / Domain | Status |
|---|---|---|---|
| AO - EDR onboarding | Onboarding | WDATP EDR onboarding | 66 Succeeded |
| AO - EDR autoupdate | autoupdate | com.microsoft.autoupdate2 | 0 Succeeded |
| AO - EDR bluetooth | bluetooth | com.microsoft.wdav.tcc.bluetooth | 0 Succeeded |
| AO - EDR Accessibility | Accessibility | com.microsoft.wdav.tcc.accessibility | 0 Succeeded |
| AO - EDR Notify | Notify | com.microsoft.wdav.notification | 0 Succeeded |
| AO - EDR BackgroundServices | BackgroundServices | com.microsoft.wdav.background | 0 Succeeded |
| AO - EDR FullDiskAccess | FullDiskAccess | com.microsoft.wdav.tcc.fulldiskaccess | 0 Succeeded |
| AO - EDR NetFilter | NetFilter | com.microsoft.wdav.webcontentfilter | 0 Succeeded |

> ⚠️ Only `AO - EDR onboarding` shows 66 Succeeded. All other EDR profiles show 0 — verify assignment and profile delivery status.

---

## 6. Device Features

| Policy Name | Assignment | Status | Last Modified |
|---|---|---|---|
| AO - Always show other user account on login screen | s_mdm_mac_temp_test | 0 Succeeded | 3/17/2025 |

**Settings:**
- Login Window > Show other users: **Yes**

---

## 7. macOS EDR (Endpoint Detection and Response)

| Policy Name | Assignment | Status |
|---|---|---|
| MacBooks-EDR Policy | All devices | 66 Succeeded |

**Settings:**
- Tag Type: GROUP
- Tag Value: *(not set)*
