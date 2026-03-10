# Endpoint Security Baseline

**Snapshot Date:** March 10, 2026  
**Defender for Endpoint Connector Status:** ✅ Enabled

## Security Categories Overview

| Category | Description | Status |
|---|---|---|
| Antivirus | Microsoft Defender Antivirus policies | Active |
| Disk Encryption | BitLocker (Windows) and FileVault (macOS) | Active |
| Firewall | Windows Firewall and macOS firewall policies | Active |
| Endpoint Privilege Management | User privilege elevation controls | Active |
| Endpoint Detection and Response | Defender for Endpoint EDR onboarding | Active |
| App Control for Business | Application control policies (AppLocker) | Active |
| Attack Surface Reduction | ASR rules for Windows devices | Active |
| Account Protection | Windows Hello, credential hardening | Active |
| Device Compliance | Compliance policies across all platforms | Active |
| Conditional Access | Policy-based access controls | ⚠️ Not configured for compliance |

---

## Attack Surface Reduction — Rule Summary

| Rule | Mode |
|---|---|
| Block PSExec and WMI process creations | Block |
| Block abuse of exploited vulnerable signed drivers | Block |
| Block all Office applications from creating child processes | Block |
| Block credential stealing from LSASS | **Audit** |
| Block rebooting machine in Safe Mode | Block |
| Block persistence through WMI event subscription | Block |
| Block untrusted and unsigned processes from USB | Block |
| Block execution of potentially obfuscated scripts | Block |
| Block Win32 API calls from Office macros | Block |
| Block JavaScript or VBScript from launching downloaded executables | Block |
| Block executable files not meeting prevalence/age/trust criteria | **Audit** |
| Block Adobe Reader from creating child processes | Block |
| Disable Autoplay on all drives | Block |

---

## BitLocker (Windows) — Active Policy

Policy: **AO - BitLocker Encryption** + **AO - Exploit Protection & Endpoint Hardening** *(passive)*

| Setting | Value |
|---|---|
| Encrypt devices | Require |
| Minimum Startup PIN Length | 6 characters (active policy) / 8 characters (hardening policy - passive) |
| Save recovery info to Entra ID | Enabled |
| Store recovery info before enabling BitLocker | Required |
| Write access to unprotected removable drives | Blocked |

> ⚠️ **BitLocker PIN policy conflict:** `BitLocker - Min startup PIN length >= 6` has 200 conflicts. Investigate overlap between this policy and `AO - Exploit Protection & Endpoint Hardening`.

---

## FileVault (macOS) — Active Policy

Policy: **AO - FileVault policy**

| Setting | Value |
|---|---|
| FileVault | Enabled |
| Force Enable In Setup Assistant | True |
| Prevent Disabling FileVault | True |
| Status | 63 Succeeded, **3 Error** |

---

## Windows Hello for Business

Policy: **AO - Account Protection policy (enable WHfB)**

| Setting | Value |
|---|---|
| Credential Guard | Enabled with UEFI lock |
| WHfB | Enabled |
| Require Security Device (TPM) | True |
| Minimum PIN Length | 6 |
| Assignment | s_mdm_Windows_Hello_Enabled |

---

## Network Protection

- **Windows:** Network Protection enabled in **block mode** (via Defender AV Hardening policy)
- **macOS:** Stealth Mode enabled; Firewall active (via AO - MacOS firewall policy)

---

## Threat Defense Connectors

| Platform | Connector Status |
|---|---|
| Windows | ✅ Active |
| iOS/iPadOS | ✅ Active |
| Android | ✅ Active |
