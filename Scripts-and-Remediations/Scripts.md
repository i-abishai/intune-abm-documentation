# Scripts and Remediations

**Snapshot Date:** March 10, 2026

---

## Remediation Script Packages (6 Packages)

| Script Package Name | Author | Status | Notes |
|---|---|---|---|
| Restart stopped Office C2R svc | Microsoft | Not deployed | — |
| AO - always on VPN (test) | AccessOrange Inc | Active | Testing phase |
| Update stale Group Policies | Microsoft | Not deployed | — |
| AO - Detect and Create `rsadmin` | AccessOrange Inc | Active | 121 OK, 12 with issue |
| Ahmet-Detection-ASR | Internal | Active | ⚠️ 15 OK, 111 with issue |
| AO - remove built-in Teams app | AccessOrange Inc | Active | 118 OK, 15 with issue |

> ⚠️ **Ahmet-Detection-ASR** has 111 devices with issues — this is likely related to the 12 profiles with assignment errors/conflicts noted in the overview.

---

## Platform Scripts (17 Scripts)

### Windows PowerShell Scripts (7)

| Script Name | Assigned | Status |
|---|---|---|
| AO - Enable WSL and VMP | No | Unassigned |
| AO - Teams firewall prompt fix | Yes | Active |
| AO - Unpin Microsoft Store Taskbar icon | Yes | Active |
| AO - autoupdate time zone | Yes | Active |
| AO - Disable File and Printer Sharing | Yes | Active |
| AO - Company Portal Desktop Shortcut | Yes | Active |
| (DISABLED) AO - set initial fixed timezone to Turkey Standard | No | Disabled |

### macOS Shell Scripts (10)

| Script Name | Assigned | Status |
|---|---|---|
| AO - install Visual Studio Code | Yes | Active |
| AO - Deploy font Barlow-SemiBold (MacOS) | Yes | Active |
| AO - Downgrade User to Standard | Yes | Active |
| AO - install Company Portal App (MacOS) | Yes | Active |
| AO - Deploy font Barlow-Medium (MacOS) | Yes | Active |
| AO - Deploy Font acuminproextracond-bolditalic (MacOS) | Yes | Active |
| AO - Create local admin account | Yes | Active |
| AO - Upgrade User to Admin | Yes | Active |
| AO - add apps to Dock | No | Unassigned |
| AO - Download Wallpaper Courts_1.png | Yes | Active |
