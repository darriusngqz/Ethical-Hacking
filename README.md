# Ethical Hacking – Enterprise Network Penetration Testing

## Overview
This repository documents an ethical hacking project conducted as part of formal coursework in penetration testing. The assignment simulates a real-world attack against a small Active Directory–based corporate network in a controlled laboratory environment. The objective was to demonstrate a full attack lifecycle, from initial access to post-exploitation and persistence, while analysing the security weaknesses that enabled each stage of the compromise. 

---

## Environment and Scenario
A realistic enterprise network was designed and deployed using VMware Workstation. The environment consisted of a Kali Linux attacker machine, a Windows Server 2019 domain controller (Victim 1), and a Windows 10 workstation joined to the domain (Victim 2), segmented across multiple subnets to simulate internal network boundaries.

The attack scenario models a situation where an attacker gains initial access through insecure wireless configurations, escalates privileges within the domain, and laterally moves to compromise additional systems.

---

## Attack Methodology
The project followed a structured penetration testing methodology aligned with real-world red team operations:

### Initial Access
Initial network access was obtained using a **Wi-Fi Evil Twin attack** with a captive portal. A rogue access point impersonated a legitimate wireless network, allowing the attacker to capture the wireless credentials of a victim user and gain access to the internal network.

### Reconnaissance and Exploitation
Once inside the network, reconnaissance and enumeration were performed to identify live hosts, open services, and domain infrastructure. A vulnerable WebDAV service hosted on the domain controller was exploited to bypass file restrictions and execute a malicious payload, granting initial shell access to the server.

### Privilege Escalation and Lateral Movement
Privileges were escalated on the compromised server through process migration and credential abuse. Network tunnelling was established to reach systems in a separate subnet. Credential harvesting and Active Directory abuse techniques were used to conduct a **Kerberos Silver Ticket attack**, allowing unauthorised access to a second domain-joined machine without valid credentials.

### Post-Exploitation
Post-exploitation activities demonstrated the real impact of the compromise, including:
- Credential harvesting and NTLM hash extraction
- Administrator hash cracking
- Accessing and extracting sensitive data from SQL databases and file systems
- Remote command execution via SMB
- Data exfiltration across network boundaries

### Persistence and Covering Tracks
Persistence mechanisms were established using **NTFS Alternate Data Streams (ADS)** and scheduled tasks running under SYSTEM privileges. Attacker operational security was demonstrated by disabling auditing, clearing Windows event logs using `auditpol` and `wevtutil`, and removing attacker tools and artefacts to hinder forensic investigation.

---

## Key Learning Outcomes
This project strengthened practical skills in:
- Ethical hacking and red team methodologies
- Wireless attacks and network-based initial access
- Active Directory exploitation and Kerberos abuse
- Post-exploitation, persistence, and attacker OPSEC
- Analysing enterprise security misconfigurations and impact

The assignment reinforced how small configuration weaknesses can be chained together to achieve full domain compromise.

---

## Responsible Use
This repository is shared strictly for educational and portfolio purposes. It does not contain live exploit code, credentials, or sensitive configuration details. All demonstrations were conducted with proper authorisation in an isolated environment.

---

## Disclaimer
All activities described were performed in a controlled lab environment for academic purposes. The author does not condone unauthorised access, exploitation, or misuse of these techniques.
