# Evidence Log

Use one row for every meaningful screenshot, command output, alert, or configuration artifact. Store screenshots in `evidence/screenshots/` using the evidence ID as the filename prefix.

| ID | Date/time and timezone | Phase | Source | Description | Related ATT&CK technique | File |
|---|---|---|---|---|---|---|
| EV-001 | 2026-09-15 17:01 (Africa/Tunis) | Network setup | VMware Virtual Network Editor | `VMnet2` configured as a host-only `192.168.50.0/24` network. The host adapter is connected and VMware DHCP is disabled, providing an isolated, statically addressed lab segment. | N/A | `evidence/screenshots/EV-001-vmnet2-isolated-network.png` |
| SW-001 | 2026-09-15 (Africa/Tunis) | Installation preparation | Ubuntu Server ISO | Local SHA-256 baseline for `ubuntu-24.04.3-live-server-amd64.iso` (3,303,444,480 bytes). User confirmed comparison with Ubuntu's published checksum. | N/A | `evidence/installer-hashes.sha256` |
| SW-002 | 2026-09-15 (Africa/Tunis) | Installation preparation | Windows 11 ISO | Local SHA-256 baseline for `Win11_25H2_English_x64.iso` (7,736,125,440 bytes). | N/A | `evidence/installer-hashes.sha256` |
| SW-003 | 2026-09-16 (Africa/Tunis) | Installation preparation | Kali Linux ISO | Local SHA-256 baseline for `kali-linux-2025.4-installer-amd64.iso` (4,733,116,416 bytes). | N/A | `evidence/installer-hashes.sha256` |
| EV-002 | 2026-09-15 17:18 (Africa/Tunis) | VM creation | VMware VM hardware settings | Wazuh server allocated 6 GB RAM and four CPU cores, with an isolated `VMnet2` adapter and a temporary NAT adapter. | N/A | `evidence/screenshots/EV-002-wazuh-vm-network-hardware.png` |
| EV-003 | 2026-09-15 17:26 (Africa/Tunis) | VM creation | VMware creation summary | Final pre-creation summary confirms Ubuntu 64-bit, an 80 GB split disk, 6 GB RAM, four CPU cores, `VMnet2`, and temporary NAT networking. | N/A | `evidence/screenshots/EV-003-wazuh-vm-creation-summary.png` |
| EV-004 | 2026-09-15 17:34 (Africa/Tunis) | Ubuntu installation | Ubuntu Server installer | `ens33` has the static lab address `192.168.50.10/24`; `ens34` received `192.168.247.143/24` from the temporary VMware NAT network. | N/A | `evidence/screenshots/EV-004-ubuntu-network-configuration.png` |
| EV-005 | 2026-09-15 18:20 (Africa/Tunis) | Ubuntu installation | Ubuntu Server installer | Installer reports successful completion and records that OpenSSH Server and security updates were installed. | N/A | `evidence/screenshots/EV-005-ubuntu-installation-complete.png` |
| EV-006 | 2026-09-15 18:36 (Africa/Tunis) | Ubuntu validation | Ubuntu Server shell | Post-installation baseline confirms hostname `wazuh-manager`, both IPv4 interfaces, 79 GB root storage, 6 GB allocated memory, active SSH service, and the `Africa/Tunis` timezone. | N/A | `evidence/screenshots/EV-006-ubuntu-post-install-validation.png` |
| EV-007 | 2026-09-15 18:38 (Africa/Tunis) | Connectivity validation | Windows PowerShell | Windows host `192.168.50.1` reached Ubuntu `192.168.50.10` on TCP port 22 through VMware Network Adapter `VMnet2`. | N/A | `evidence/screenshots/EV-007-host-to-ubuntu-ssh-connectivity.png` |
| EV-008 | 2026-09-15 18:51 (Africa/Tunis) | Ubuntu baseline | Ubuntu Server shell | Updated baseline confirms kernel `6.8.0-139-generic`, active SSH and VMware Tools services, and both expected network interfaces. Four coordinated Netplan packages remained eligible for Ubuntu's phased update rollout; no packages were held. | N/A | `evidence/screenshots/EV-008-ubuntu-updated-baseline.png` |
| EV-009 | 2026-09-15 21:34 (Africa/Tunis) | Ubuntu baseline | VMware Snapshot Manager | Powered-off snapshot `00-clean-os-updated` created before Wazuh installation, providing a recovery point for the clean Ubuntu baseline. | N/A | `evidence/screenshots/EV-009-ubuntu-clean-baseline-snapshot.png` |
| EV-010 | 2026-09-15 21:46 (Africa/Tunis) | Windows VM creation | VMware creation summary | Windows 11 victim VM configured with two CPU cores, 4 GB RAM, a 64 GB split disk, isolated `VMnet2`, and temporary NAT networking. TPM encryption, UEFI Secure Boot, and the installer ISO were confirmed separately before startup. | N/A | `evidence/screenshots/EV-010-windows-vm-creation-summary.png` |
| EV-011 | 2026-09-16 11:17 (Africa/Tunis) | Windows configuration | Administrator PowerShell | Hostname `WIN11-VICTIM` uses static `192.168.50.20/24` on private `SOC-LAB`; only the public temporary NAT interface has a default route and Internet connectivity. | N/A | `evidence/screenshots/EV-011-windows-network-configuration.png` |
| EV-012 | 2026-09-16 11:47 (Africa/Tunis) | Windows baseline | Windows Update | Windows Update reports the endpoint is up to date after initial installation and required updates. Early-access non-security updates remain disabled. | N/A | `evidence/screenshots/EV-012-windows-update-current.png` |
| EV-013 | 2026-09-16 11:51 (Africa/Tunis) | Windows security baseline | Administrator PowerShell | Secure Boot and TPM readiness confirmed; VMware Tools and Microsoft Defender run automatically; Defender antivirus, real-time protection, and behavior monitoring are enabled. | N/A | `evidence/screenshots/EV-013-windows-security-baseline.png` |
| EV-014 | 2026-09-16 11:53 (Africa/Tunis) | Windows baseline | VMware Snapshot Manager | Powered-off snapshot `00-clean-os-updated` created before Wazuh agent and Sysmon installation, providing a clean Windows recovery point. | N/A | `evidence/screenshots/EV-014-windows-clean-baseline-snapshot.png` |

## Evidence-handling notes

- Preserve the original screenshot or exported event.
- Save new screenshots directly in `evidence/screenshots/` using the assigned ID and a short descriptive name.
- If a screenshot is initially saved elsewhere, provide its exact path so it can be copied into the project.
- Redact secrets without changing security-relevant details.
- Record commands exactly as executed.
- Use Tunis local time (`Africa/Tunis`) consistently and note VM clock differences.
- Explain what each artifact proves; do not rely on screenshots alone.
