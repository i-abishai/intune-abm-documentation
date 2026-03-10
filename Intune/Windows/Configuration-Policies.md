# Windows Configuration Policies

**Total Policies (Windows):** 53 | **Last Snapshot:** March 10, 2026

---

## 1. Attack Surface Reduction (ASR) Rules

| Policy Name | Mode | Status | Last Modified |
|---|---|---|---|
| 4 - ASR - Block - ALL DEVICE - PSExec-WMI | Block | 198 Succeeded | 2/4/2026 |
| 10 - ASR - Audit - ALL DEVICE - Vulnerable signed drivers | Block | 200 Succeeded | 2/3/2026 |
| 9 - ASR - Audit - ALL DEVICE - Office communication apps | Block | 220 Succeeded | 12/26/2025 |
| ASR - AUDIT - ALL DEVICE - LSASS | Audit | 220 Succeeded | 12/26/2025 |
| 13 - ASR - Block - ALL DEVICE - SafeModeReboot | Block | 220 Succeeded | 12/26/2025 |
| 8 - ASR - Audit - ALL DEVICE - WMI persistence | Block | 220 Succeeded | 12/26/2025 |
| 7 - ASR - Audit - ALL DEVICE - USB unsigned | Block | 220 Succeeded | 12/26/2025 |
| 5 - ASR - Audit - ALL DEVICE - Obfuscated scripts | Block | 220 Succeeded | 12/26/2025 |
| 3 - ASR - Block - ALL DEVICE - Office macro Win32 | Block | 220 Succeeded | 12/26/2025 |
| 2 - ASR - Block - ALL DEVICE - JS-VBS downloaded exe | Block | 220 Succeeded | 12/26/2025 |
| ASR - Audit - ALL DEVICE - Prevalence-age-trust-6 | Audit | 220 Succeeded | 12/22/2025 |
| ASR - Block - ALL DEVICE - Disable Autoplay -12 | Block | 219 Succeeded | 12/22/2025 |
| Block Adobe Reader from creating child processes | Block | 222 Succeeded | 12/11/2025 |

### Policy Detail: PSExec-WMI Block

- **Assignment:** All devices (Active)
- **Setting:** Block process creations originating from PSExec and WMI commands → **Block**
- **Exclusions:** Setup executable (MLM2ProRefurbishAppv1.0.2-Setup.exe)

### Policy Detail: LSASS Audit

- **Assignment:** All devices (Active)
- **Setting:** Block credential stealing from the Windows local security authority subsystem → **Audit**
- **Purpose:** Prevents Mimikatz-style credential dumping; critical for lateral movement defense.

### Policy Detail: Disable Autoplay

- **Settings (Administrative Templates > AutoPlay Policies):**
  - Turn off Autoplay on: **All drives**
  - Default AutoRun behavior: **Do not execute any autorun commands**
  - Turn off Autoplay: **Enabled**

---

## 2. Device Control

| Policy Name | Description | Assignment | Last Modified |
|---|---|---|---|
| Block_USB_FACTORY | Block USB for external factory production devices | Factory-Test-Laptop | 1/28/2026 |

- **Setting:** Removable Disk Deny Write Access → **Enabled**

---

## 3. Wi-Fi Profiles

| Policy Name | SSID | Security | Assignment | Status |
|---|---|---|---|---|
| AM_SG_Corporate_WiFi | [CORP-SSID-SG] | WPA/WPA2-Personal | s_mdm_wifi_sg_policy | 53 Succeeded, 67 Error |
| AM_SG_Dev_WiFi | [DEV-SSID-SG] | WPA/WPA2-Personal | None (unassigned) | 0 |
| AM_SG_CLevel_WiFi | [CLEVEL-SSID-SG] | WPA/WPA2-Personal | None (unassigned) | 0 |
| AM_SG_Guest_WiFi | [GUEST-SSID-SG] | WPA/WPA2-Personal | None (unassigned) | 0 |
| AO - Wifi Profile (SG)(Windows) | [CORP-SSID-SG] | WPA/WPA2-Personal | — | — |

> ⚠️ **AM_SG_Corporate_WiFi** has 67 errors — assignment or authentication issue requires investigation.

**Common Settings (Corporate Wi-Fi):**
- Wi-Fi type: Basic
- Connect automatically: Yes
- Broadcast SSID hidden: No
- Metered Connection: Unrestricted
- Pre-shared key: *(masked)*
- Force FIPS compliance: No
- Proxy: None

---

## 4. Endpoint Protection

| Policy Name | Assignment | Status | Last Modified |
|---|---|---|---|
| ExploitProtection - ALL DEVICE - AUDIT - recommendation 15 | All Devices | 219 Succeeded | 12/22/2025 |
| AO - Exploit Protection & Endpoint Hardening | Unassigned | 0 | 11/28/2025 |

### Policy Detail: ExploitProtection AUDIT

- **Folder protection:** Audit only

### Policy Detail: AO - Exploit Protection & Endpoint Hardening *(Passive — no assignment)*

**Microsoft Defender SmartScreen:**
- SmartScreen for apps and files: Enable
- Unverified files execution: Block

**Windows Encryption (BitLocker):**
- Encrypt devices: Require
- Warning for other disk encryption: Block
- Minimum PIN Length: 8
- Save BitLocker recovery info to Entra ID: Enable
- Store recovery info in Entra ID before enabling BitLocker: Require
- Write access to removable drive not protected by BitLocker: Block

**Microsoft Defender Exploit Guard:**
- Folder protection: Enable

**Microsoft Defender Security Center:**
- Tamper Protection: Enabled
- IT Contact: it@[REDACTED-DOMAIN] | Help desk: [internal-ITSM-URL]

**Local Security Options:**
- Anonymous access to Named Pipes and Shares: Block
- LAN Manager hash stored on password change: Block
- Insecure Guest Logons: Block
- Clear virtual memory pagefile on shutdown: Enabled
- Digitally sign communications (always): Enable

**Xbox Services (all disabled):** Xbox Accessory Management, Xbox Live Auth Manager, Xbox Live Game Save, Xbox Live Networking

---

## 5. Defender Antivirus

### WIN - Defender AV Hardening - v1

- **Assignment:** All devices (Active) | **Status:** 222 Succeeded

| Setting | Value |
|---|---|
| Allow Archive Scanning | Allowed |
| Allow Behavior Monitoring | Allowed |
| Allow Cloud Protection | Allowed |
| Allow Email Scanning | Not allowed |
| Allow Full Scan On Mapped Network Drives | Not allowed |
| Allow Full Scan Removable Drive Scanning | Allowed |
| Allow Realtime Monitoring | Allowed |
| Allow Scanning Network Files | Not allowed |
| Allow Script Scanning | Allowed |
| Cloud Block Level | High |
| Enable Network Protection | Enabled (block mode) |
| PUA Protection | Block |
| Real Time Scan Direction | Monitor all files (bi-directional) |
| Scan Parameter | Quick scan |
| Schedule Scan Day | Monday |
| Signature Update Interval | 2 hours |
| Submit Samples Consent | Send safe samples automatically |

### NGP Windows default policy *(Unassigned)*

- **Purpose:** Fallback policy for any endpoint not governed by another policy.
- Key differences from Hardening v1: Cloud Block Level = Default, PUA Protection = Off, Signature Update Interval = 4 hrs.

---

## 6. Settings Catalog

| Policy Name | Description | Assignment | Status | Last Modified |
|---|---|---|---|---|
| BitLocker - Min startup PIN length >= 6 | Minimum 6-char BitLocker PIN | All devices | ⚠️ 19 Succeeded, 200 Conflict | 12/22/2025 |
| AM: Outlook Safe Senders Policy | Safe Senders list path | Unassigned | 0 | 11/12/2025 |
| AO - browser main page (US) | Sets browser homepage to US SharePoint | s_mdm_winUsers_us | 38 Succeeded | 9/17/2025 |
| AO - Disable Touch input (testing) | Disables tablet touch input | s_mdm_dev_noTouchScreen | 1 Succeeded | 2/3/2025 |
| AO - OneDrive policy (Windows) | OneDrive configuration | — | — | 11/1/2023 |
| AO - PS Script Block Logging (Windows) | Enables PowerShell Script Block Logging | — | — | 11/1/2023 |
| AO - Block Wi-Fi Internet Sharing (Windows) | Blocks Wi-Fi hotspot sharing | — | — | 11/1/2023 |
| AO - Windows App Store policy (Windows) | Controls Microsoft Store access | — | — | 11/17/2023 |
| AO - Allow apps from the Microsoft Store | Allow Store apps | — | — | 11/14/2023 |
| AO - Set Google as default search for Edge | Edge default search engine | — | — | 11/14/2023 |
| AO - disable Teams Chat icon on taskbar | Removes Teams Chat from taskbar | — | — | 12/5/2023 |
| AO - Enforce location service for auto timezone | Auto timezone via location | — | — | 12/19/2023 |
| Disable Chat Icon Settings Catalog | Removes Chat icon | — | — | 7/28/2023 |

> ⚠️ **BitLocker PIN policy** has 200 conflicts — likely conflicting with another BitLocker policy. Investigate overlap with `AO - BitLocker Encryption`.

---

## 7. Firewall

| Policy Name | Assignment | Status | Last Modified |
|---|---|---|---|
| Default Firewall policy | All devices (Excl: s_mdm_policies_firewall_exception) | 261 Succeeded | 10/10/2023 |
| AO - Firewall | s_mdm_winUsers (Excl: s_apps_dev, s_mdm_win_firewall_ex) | 85 Succeeded | 12/27/2024 |
| WIN - Firewall Hardening - v1 | Unassigned | 0 | 11/28/2025 |

**Default Firewall Policy Settings (All Profiles):**
- Domain / Private / Public: Firewall Enabled
- Default Inbound Action: **Block**
- Default Outbound Action: **Allow**

**WIN - Firewall Hardening - v1 Additional Settings:**
- Log File Path: `%systemroot%\system32\LogFiles\Firewall\pfirewall.log`
- Log Max File Size: 1024 KB
- Stealth Mode: Enabled (Disable Stealth Mode = False)
- Log Dropped Packets: Disabled (logging off)
- Log Success Connections: Disabled (logging off)

---

## 8. Account Protection

### AO - Account Protection policy (enable WHfB)

- **Assignment:** s_mdm_Windows_Hello_Enabled | **Status:** 56 Succeeded

| Setting | Value |
|---|---|
| Credential Guard | Enabled with UEFI lock |
| Use Windows Hello For Business | True |
| Require Security Device | True |
| Minimum PIN Length | 6 |

### WIN - Account Protection Hardening *(Passive — no assignment)*

| Setting | Value |
|---|---|
| Credential Guard | Enabled with UEFI lock |
| Use Windows Hello For Business | True |
| Minimum PIN Length | 8 |
| PIN Expiration | 180 days |
| PIN History | 5 |
| Uppercase Letters | Required |
| Lowercase Letters | Required |
| Special Characters | Required |
| Anti-Spoofing (Face) | True |
| PIN Recovery | Enabled |

---

## 9. Other Policies

| Policy Name | Type | Assignment | Status | Last Modified |
|---|---|---|---|---|
| LSA Protection (PPL) - Remediate | Custom OMA-URI | GRP - LSA-PPL - Remediate | 9 Succeeded | 12/22/2025 |
| AO - Applocker policy (Windows) | Custom | s_mdm_winUsers (Excl: applocker test, s_apps_dev) | 35 Succeeded | 11/22/2024 |
| AO - applocker test | Custom | Intune_test_windows_applocker | 50 Succeeded | 11/19/2024 |
| Overall | Elevation settings policy | — | — | 10/3/2024 |
| Default EDR policy for all devices | EDR | — | — | 12/12/2023 |
| Intune data collection policy | Windows health monitoring | — | — | 11/23/2023 |
| AO - BitLocker Encryption | BitLocker | — | — | 10/16/2023 |
| AO - Disable Windows Hello (Windows) | Identity protection | — | — | 11/1/2023 |
| AO - Power Management (Windows) | Administrative templates | — | — | 11/1/2023 |
| AO - Google Chrome & Edge Bookmarks | Administrative templates | s_mdm_winUsers | 107 Succeeded | — |

**LSA Protection OMA-URI:**
- OMA-URI: `./Device/Vendor/MSFT/Policy/Config/LocalSecurityAuthority/ConfigureLsaProtectedProcess`
- Value type: Integer

**AppLocker Policy Rules:**
- Windows Installer Rule: `./Vendor/MSFT/AppLocker`
- Packaged App Rule: `./Vendor/MSFT/AppLocker`
- EXE Rule: `./Vendor/MSFT/AppLocker`
