# 🔐 Brute Force Attack Simulation (SOC Detection & Analysis)

## Overview
This project demonstrates the detection and investigation of **brute force authentication activity** in a controlled lab environment using **Windows Security Event Logs** and **Wazuh SIEM**.

The focus of this project was not exploitation, but **SOC-style alert triage, investigation, correlation, and decision-making**, mirroring how brute force attacks are handled in real Security Operations Centers.

---

## Lab Environment

- **Victim System:** Windows 11
- **SIEM / Monitoring:** Wazuh
- **Log Source:** Windows Security Event Logs
- **Attack Simulation:** Controlled authentication misuse (safe, local simulation)

### Relevant Windows Events
- **4625** – Failed logon
- **4624** – Successful logon
- **4740** – Account lockout

---

## Simulation Description

### Scenario
A simulated brute force attack was conducted by repeatedly attempting authentication against a Windows user account using invalid credentials, followed by a valid login attempt.

The objective was to:
- Generate realistic brute force telemetry
- Observe authentication patterns over time
- Practice SOC-level analysis and classification

---

## Detection & Investigation Workflow

Each authentication alert was investigated using the following SOC pivots:

- Targeted user account
- Source workstation / IP
- Logon type (interactive, network, RDP)
- Frequency and timing of events
- Correlation between failures, lockouts, and success

This workflow allowed accurate separation of **noise**, **suspicious behavior**, and **true brute force activity**.

---

## Screenshots / Evidence

> 📸 *Screenshots captured during investigation*

Recommended inclusions:
- Wazuh event view showing repeated **4625** failures
- Expanded event details highlighting logon type and source
- Timeline correlation of failures → success or lockout

```text
[Screenshot Placeholder – Repeated Failed Logons (4625)]
![Kali Linux Dragon](Repeated Failed Logons.png)
[Screenshot Placeholder – Expanded Authentication Event]
[Screenshot Placeholder – Correlated Brute Force Timeline]
