# Wazuh SOC Home Lab

Design and implementation of an isolated Security Operations Center home lab for threat hunting, malware detection, incident investigation, and MITRE ATT&CK mapping.

## Lab components

| System | Purpose | Lab address |
|---|---|---|
| Ubuntu Server | Wazuh manager, indexer, and dashboard | `192.168.50.10` |
| Windows 11 | Monitored victim endpoint | `192.168.50.20` |
| Kali Linux | Authorized attack-simulation host | `192.168.50.30` |
| Windows host | VMware host and dashboard access | `192.168.50.1` (expected) |

The final addresses will be confirmed after the VMware virtual network is created.

## Project phases

- [ ] Phase 0 — Define scope, safety rules, and success criteria
- [ ] Phase 1 — Install VMware and build an isolated network
- [ ] Phase 2 — Install and baseline the three virtual machines
- [ ] Phase 3 — Deploy Wazuh and enroll the Windows agent
- [ ] Phase 4 — Add endpoint telemetry and malware-detection controls
- [ ] Phase 5 — Execute safe adversary simulations
- [ ] Phase 6 — Threat hunt, investigate, and tune detections
- [ ] Phase 7 — Produce the final report and presentation material

## Planned detection scenarios

1. Network reconnaissance and port scanning
2. Authentication failure and password-guessing activity
3. Suspicious PowerShell execution
4. File-integrity monitoring and EICAR test-file detection
5. Persistence simulation
6. Credential-access simulation using safe test techniques
7. Windows Defender and Sysmon alert correlation
8. Optional active response and malicious-IP enrichment

All tests must remain inside the private lab and use safe simulations or inert test artifacts.

## Documentation

- [Architecture and setup](docs/01-architecture-and-setup.md)
- [Evidence log](docs/evidence-log.md)
- [Final report draft](report/report.md)

