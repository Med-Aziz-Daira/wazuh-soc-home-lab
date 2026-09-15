# Design and Implementation of a Wazuh-Based SOC Home Lab for Threat Hunting and Malware Detection

**Author:** TBD  
**Date:** TBD  

## Abstract

This report documents the design, deployment, and evaluation of an isolated SOC home lab based on Wazuh. The environment contains a Wazuh server, a Windows 11 monitored endpoint, and a Kali Linux adversary-simulation host. Safe attack simulations are used to validate telemetry collection, malware detection, threat hunting, alert investigation, and MITRE ATT&CK mapping.

## 1. Introduction

### 1.1 Background

TBD

### 1.2 Problem statement

TBD

### 1.3 Objectives

- Build an isolated and reproducible SOC laboratory.
- Centralize security telemetry from a Windows endpoint.
- Detect and investigate representative malicious behaviors.
- Map observed behaviors and detections to MITRE ATT&CK.
- Evaluate detection coverage, false positives, and limitations.

### 1.4 Scope and ethical boundaries

Testing is restricted to systems owned by the author and connected to the isolated lab network. The project uses safe simulations and inert test files. No attack is directed at public services, third-party systems, or the physical local-area network.

## 2. Technical Background

### 2.1 Security operations and SIEM/XDR concepts

TBD

### 2.2 Wazuh architecture

TBD

### 2.3 Endpoint telemetry and Sysmon

TBD

### 2.4 MITRE ATT&CK

TBD

## 3. Requirements and Architecture

### 3.1 Hardware and software requirements

TBD

### 3.2 Network design and isolation

TBD

### 3.3 Risk assessment

TBD

## 4. Implementation

### 4.1 Virtual environment

TBD

### 4.2 Wazuh deployment

TBD

### 4.3 Windows agent and telemetry configuration

TBD

### 4.4 Detection and enrichment configuration

TBD

## 5. Detection Scenarios

For every scenario, document the objective, ATT&CK mapping, prerequisites, exact procedure, expected telemetry, Wazuh result, evidence, cleanup, and limitations.

### 5.1 Network reconnaissance

TBD

### 5.2 Authentication attacks

TBD

### 5.3 Suspicious PowerShell behavior

TBD

### 5.4 Malware and file-integrity detection

TBD

### 5.5 Persistence behavior

TBD

## 6. Threat Hunting and Incident Investigation

TBD

## 7. Results and Evaluation

Include detection rate, alert latency, false positives, resource consumption, ATT&CK coverage, and detection gaps.

## 8. Limitations and Recommendations

TBD

## 9. Conclusion

TBD

## References

TBD

## Appendices

### Appendix A — Address plan

TBD

### Appendix B — Configuration excerpts

TBD

### Appendix C — Detection test matrix

TBD

