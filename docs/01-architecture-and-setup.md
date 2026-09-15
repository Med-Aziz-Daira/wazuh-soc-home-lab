# Architecture and Setup

## Design decision

The lab uses a VMware host-only network instead of bridged networking. Bridged networking would expose attack traffic to the physical household or campus network. The host-only network provides isolation while allowing the Windows host to open the Wazuh dashboard.

A second NAT adapter may be attached temporarily for operating-system updates and package installation. It should be disconnected from attack machines during simulations unless a documented test requires internet access.

```text
                         Temporary update path
                              VMware NAT
                                  |
     Windows host                | (disconnect during tests)
   192.168.50.1                  |
          |                      |
==========+================================================
        VMnet: SOC-LAB (host-only, 192.168.50.0/24)
          |                       |                    |
   Wazuh server            Windows victim          Kali attacker
  192.168.50.10           192.168.50.20         192.168.50.30
```

## Resource allocation

The laptop has 16 GB RAM and an Intel Core i5 12th-generation CPU with 8 cores and 12 logical processors. CPU capacity is adequate; memory is the limiting resource.

| Virtual machine | Memory | vCPU | Thin-provisioned disk |
|---|---:|---:|---:|
| Ubuntu/Wazuh | 6 GB | 4 | 80 GB |
| Windows 11 | 4 GB | 2 | 64 GB |
| Kali Linux | 2 GB | 2 | 40 GB |

Kali should be powered off when it is not needed. Snapshots require additional host storage, so at least 120 GB of real free disk space is recommended even with thin provisioning.

## VMware network configuration

After VMware Workstation Pro is installed:

1. Open **Edit > Virtual Network Editor** as administrator.
2. Create or repurpose a custom network such as `VMnet2`.
3. Select **Host-only**.
4. Set the subnet to `192.168.50.0` with mask `255.255.255.0`.
5. Disable VMware DHCP so that the lab uses documented static addresses.
6. Keep `VMnet8` as NAT for temporary updates.
7. Give each VM one adapter on custom network `VMnet2`.
8. Add a second NAT adapter only during installation and updates.
9. Never attach the Kali VM to a bridged adapter for this project.

VMware may assign the host-side adapter an address other than `192.168.50.1`. Verify it with `ipconfig` and record the actual value in the evidence log.

## Recommended operating systems

- Ubuntu Server LTS, 64-bit, minimal installation
- Windows 11 evaluation or properly licensed installation
- Kali Linux installer image, 64-bit

Exact release numbers, checksums, download URLs, and installation dates must be recorded for reproducibility. Wazuh compatibility with the chosen Ubuntu release must be checked against its current official documentation before installation.

## Initial checkpoint

Before installing Wazuh, confirm:

- All three VMs boot successfully.
- Static IP addresses are configured.
- Each VM can ping the other two on the private network.
- The Windows host can reach `192.168.50.10`.
- Internet access works only through the temporary NAT adapters.
- Baseline snapshots have been created after updates.

Suggested snapshot names:

- `00-clean-os-updated`
- `01-network-configured`
- `02-before-wazuh-agent`

## Evidence to capture

- VMware Virtual Network Editor showing the isolated subnet
- VM hardware settings for each machine
- `ipconfig` on Windows and `ip addr` on Linux
- Successful private-network connectivity tests
- Snapshot Manager showing baseline snapshots

Do not include passwords, API keys, personal IP addresses, or unrelated host information in screenshots.

