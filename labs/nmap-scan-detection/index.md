---
title: Network Scanning Probe Attack and Detection
permalink: /labs/nmap-scan-detection/
---

- [Learning Objectives](#learning-objectives)
- [Lab Setup](#lab-setup)
- [Logical Network Diagram](#logical-network-diagram)
- [Software](#software)
- [Attack Simulation](#attack-simulation)
- [Output](#output)
- [Conclusion](#conclusion)
- [Link Tree](#link-tree)

## Learning Objectives
***
 - Understand Nmap, a popular network scanner, and its capabilities.
 - Simulate network scanning attacks with Nmap.
 - Verify the effectiveness of Suricata IDS rules in detecting scans.
 - Visualize Suricata alerts on the Wazuh dashboard for analysis.

## Lab Setup
***
### Components:
 - Attacker machine (Ubuntu Desktop Hosted on VMWare)
 - Target machine (Ubuntu Server Hosted on VMWare) with Wazuh agent and Suricata installed
 - Wazuh server (Ubuntu Server Hosted on Google Cloud Platform)

## Logical Network Diagram
***
![Network Scanning Probe Attack and Detection drawio](https://github.com/user-attachments/assets/0b9e0f98-f644-4e20-974a-61a33993e876)

## Software
***
 - Nmap
 - Wazuh
 - Suricata
  
## Attack Simulation
***
1. Scanning for Open Ports (SYN Scan):
- Open a terminal on the attacker machine and run: nmap -sS -Pn 10.0.2.5  // Replace with target IP
- This command performs a SYN scan (half-open) to identify open ports on the target machine.
2. Scanning for Software Versions (Version Scan):
- Run the following command to identify software versions: nmap -sS -sV -Pn 10.0.2.5 // Replace with target IP
- This command combines a SYN scan with a version scan.

## Output
***
The output will display discovered open ports and potentially software versions running on the target machine.

![NmapScan](https://github.com/user-attachments/assets/ec54b462-7ad4-4eab-a294-7ab279db1360)

### Wazuh Alert Visualization
1. Login to the Wazuh manager and navigate to "Security Events".
2. Select the target machine (Wazuh agent) from the list.
3. You should see Suricata alerts generated for the detected network scanning attempts.

### Filtering Alerts:
- Use the filter rule.group: suricata to focus on Suricata-related alerts.
![WazuhNmapEvents](https://github.com/user-attachments/assets/8a68c22c-1ada-44e3-ad1b-569be84e2243)

### Alert Details:
Expand an alert for details such as:
- Rule signature (e.g., ET SCAN Potential SSH Scan OUTBOUND)
- Source and destination IP addresses
- Action taken by Wazuh
- Severity level of the event

## Conclusion
***
This project demonstrates how Suricata effectively detects network scanning probes using the ET ruleset. Wazuh visualizes these alerts, allowing security personnel to identify potential threats and investigate further.
### Additional Notes:
 - Network scanning is a legitimate tool for network administrators, but malicious actors also utilize it for reconnaissance.
 - Suricata provides a robust way to detect suspicious scanning activity on your network.
 - Wazuh enhances security posture by offering centralized management and visualization of security events.

## Link Tree
***

{% include linktree.html %}
