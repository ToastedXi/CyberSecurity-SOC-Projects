# 🔐 Brute Force Attack Simulation (SOC Detection & Analysis)

## Overview
This project demonstrates the detection and investigation of **brute force authentication activity** in a controlled lab environment using **Windows Security Event Logs** and **Wazuh SIEM**.

The focus of this project was not exploitation, but **SOC style alert triage, investigation, correlation, and decision making**, mirroring how brute force attacks are handled in real Security Operations Centers.

---

## Lab Environment
- **Victim System:** Windows 11
- **SIEM / Monitoring:** Wazuh
- **Log Source:** Windows Security Event Logs
- **Attack Simulation:** Controlled authentication misuse (safe, local simulation)

### Relevant Windows Events
- **4625** – An account failed to log on
- **4624** – An account was successfully logged on

---

## Simulation Description
### Scenario
A simulated brute force attack was conducted by repeatedly attempting authentication against a Windows user account using invalid credentials, followed by a valid login attempt.

The objective was to:
- Generate realistic brute force telemetry
- Observe authentication patterns over time
- Practice SOC level analysis and classification

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

### Repeated Failed Logons (Event ID 4625)
![Wazuh dashboard showing repeated Event ID 4625 failed logon alerts](Repeated%20Failed%20Logons.png)

### Expanded Authentication Event
![Detailed view of a single Event ID 4625 with logon type, source IP, and failure reason](Expanded%20Authentication.png)

### Correlated Brute Force Timeline
![Timeline correlating repeated failed logons leading to potential success or lockout](Correlated%20Brute%20Force.png)

---

## Key Learnings from This Brute Force Simulation
Through hands on simulation and analysis in my SOC Lab journey, I gained practical insights into real world threat detection:

- **Pattern Recognition:** Brute force isn't just high volume failures, it's about rapid, repetitive attempts from the same source targeting one account. Distinguishing this from legitimate mistypes or misconfigurations is critical.
- **Event Correlation:** Single 4625 events are noisy; true positives emerge when correlating with timing, source IP, logon type, and follow-up events (e.g., 4624 success or 4740 lockout).
- **SIEM Tuning & Alert Fatigue:** Default rules catch basics, but custom Wazuh decoders/rules can reduce false positives by thresholding frequency and ignoring known benign sources.
- **Investigation Efficiency:** Quick pivots (user → source → timeline) speed up triage from minutes to seconds.
- **Attack Variants:** Learned differences between online (RDP/network) vs. offline brute force, password spraying, and credential stuffing each leaves distinct footprints.

This deepened my understanding of authentication based threats beyond theory.

---

## Value I Can Now Deliver to Companies
As part of building my SOC skillset, this lab equips me to contribute immediately in real environments:

- **Effective Alert Triage:** Rapidly investigate and classify brute force alerts, reducing mean-time to detect (MTTD) and preventing escalation.
- **Threat Hunting:** Proactively query logs for subtle brute force variants (e.g., slow/low-volume spraying across accounts).
- **Rule Development:** Create or tune SIEM detection rules (Sigma, Wazuh, ELK) for better coverage of authentication attacks.
- **Incident Response Support:** Provide clear, evidence based reporting during incidents, including timelines and indicators.
- **Security Recommendations:** Advise on mitigations like account lockout policies, MFA enforcement, IP allowlisting, and monitoring enhancements.

I'm continuing my SOC Lab journey with more scenarios (e.g., lateral movement, phishing, EDR alerts) to build a well-rounded blue team portfolio.

---

*Part of my ongoing SOC Analyst Lab Series – Building practical blue team skills, one detection at a time.*
