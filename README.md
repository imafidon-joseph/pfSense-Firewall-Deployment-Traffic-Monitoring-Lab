# Network Security Monitoring Lab: pfSense Firewall, Suricata IDS, and Splunk SIEM Integration


# Project Overview
This project demonstrates the deployment of a layered network security lab integrating a pfSense firewall, Suricata IDS, and Splunk SIEM. A firewall was configured to enforce traffic control through custom block rules, while Suricata monitored and detected suspicious activities such as network scans. The generated logs were forwarded to Splunk for centralized analysis, enabling effective threat detection and investigation. This setup reflects real-world SOC workflows involving firewall management, intrusion detection, and SIEM-based monitoring.

The objective is to simulate real-world network security operations by implementing firewall rules, generating traffic, and analyzing logs as a Security Operations Center (SOC) analys

# Objectives

* Deploy and configure a pfSense firewall
* Implement network segmentation and traffic control
* Create and enforce firewall block rules
* Set up Suricata IDS for real-time intrusion detection
* Detect network attacks such as Nmap scanning
* Forward and centralize logs using Splunk SIEM
* Monitor and analyze security events from Suricata logs
* Simulate attacker behavior using Kali Linux
* Investigate alerts and understand threat patterns
* Gain hands-on experience with real-world SOC workflows

# Lab Architecture

* Kali Linux (Attacker)
*    ↓
* pfSense Firewall
*    ↓
* Target Machine (Victim)

# Tools & Environment

* pfSense Firewall (Network security and traffic filtering)
* Suricata IDS/IPS (Intrusion detection and monitoring)
* Splunk SIEM (Log collection, analysis, and visualization)
* Kali Linux (Attacker machine for simulation)
* Target Machine (Victim system for testing)
* VirtualBox (Virtualization environment)
* Nmap (Network scanning and reconnaissance tool)

# pfSense Installation

* Created a virtual machine in VirtualBox
* Installed pfSense using ISO image
* Assigned WAN and LAN interfaces

  **pfSense dashboard**

<img width="1600" height="742" alt="2026_04_30_22_43_10_IMG_3323" src="https://github.com/user-attachments/assets/4d677e9c-0106-41cb-847e-eaf7a0d8de9d" />

<img width="1600" height="742" alt="2026_04_30_22_43_15_IMG_3324" src="https://github.com/user-attachments/assets/81fa3df2-73b0-4b0b-92e8-ecf598d43aa3" />

# Firewall Rule Configuration

**I Created rules to control traffic between attacker and target**

<img width="1600" height="742" alt="2026_04_30_22_43_25_IMG_3326" src="https://github.com/user-attachments/assets/17c3d9b0-9ece-4f51-8298-7055514d098e" />

**Ping Test before i blocked it with pfSense firewall**

<img width="1600" height="742" alt="2026_04_30_22_43_20_IMG_3325" src="https://github.com/user-attachments/assets/2e7fb591-7d3b-4447-b204-e95cfe7968b5" />

**I bocked ICMP Packet from external network**

<img width="1600" height="742" alt="2026_04_30_22_43_52_IMG_3329" src="https://github.com/user-attachments/assets/26ddcc2a-1f3f-4077-b2d2-69c4bf3d0b1b" />

**Ping Test After i blocked it with pfSense firewall**

<img width="1600" height="206" alt="new edit" src="https://github.com/user-attachments/assets/0298398f-5350-40e6-98af-a79ff34418b5" />

# pfSense log dashboard

**Firewall logged all blocked traffic from the ping attempt**

<img width="1599" height="717" alt="2026_04_30_22_44_23_IMG_3333" src="https://github.com/user-attachments/assets/66161b9a-1385-4e69-821a-7150143847f1" />

**Key Observations**

* Firewall successfully controlled network traffic
* Blocked rules prevented unauthorized access
* Logs provided visibility into network activity
* Attack attempts were clearly recorded

# Suricata Installation

<img width="1600" height="742" alt="2026_04_30_22_44_55_IMG_3334" src="https://github.com/user-attachments/assets/5ac83ac0-aa2d-4e73-b093-b2cca507670d" />

* Installed Suricata package via pfSense package manager
* Enabled Suricata on the LAN interface
* Configured logging and alerting features

# Rule Configuration

<img width="1600" height="742" alt="2026_04_30_22_45_01_IMG_3335" src="https://github.com/user-attachments/assets/764eac60-c77a-4828-b466-0bba100cbb3a" />

* Enabled Emerging Threats (ET) Open ruleset
* Selected relevant categories including: emerging-scan.rules
* Updated rules to ensure latest threat signatures

# Detection and Analysis

**Suricata successfully detected and logged multiple scanning activities.**

<img width="1600" height="742" alt="2026_04_30_22_45_11_IMG_3337" src="https://github.com/user-attachments/assets/e6ba373d-fd74-40ab-a6e3-cb5b6d4aeb41" />

**Sample Alert Details:**

* Source IP: 192.168.1.100
* Destination IP: 192.168.1.1
* Protocol: TCP
* Port: 80
* Alert Message:
    ET SCAN Possible Nmap User-Agent Observed

# Analysis

**The alerts indicate that Suricata correctly identified:**

* Reconnaissance behavior
* Signature-based detection of Nmap scans
* Multiple scan techniques targeting open services

This confirms that the IDS is functioning effectively in detecting suspicious activity.

# Log Management and SIEM Integration (Splunk)

To enhance visibility and enable centralized log analysis, Suricata logs were integrated with Splunk, a Security Information and Event Management (SIEM) platform. This allowed real-time monitoring, searching, and analysis of network security events generated by the firewall IDS.

# Configuration Steps

**Enable Logging in Suricata**

* Enabled EVE JSON logging in Suricata settings
* Configured logs to capture:
    * Alerts
    * HTTP traffic
    * Flow data

# Log Analysis in Splunk

After successful ingestion, pfSense firewall log and Suricata alerts were visible in Splunk.

<img width="1600" height="742" alt="2026_04_30_22_45_27_IMG_3340" src="https://github.com/user-attachments/assets/c40a3b3c-69c0-4138-bc15-371e31eede6c" />

<img width="1600" height="742" alt="2026_04_30_22_45_31_IMG_3341" src="https://github.com/user-attachments/assets/40e1a159-8bec-4b18-9ac6-dae9bb89e258" />

# Benefits of Splunk Integration

* Centralized log management
* Faster threat investigation
* Improved visibility across network events
* Ability to create dashboards and alerts
* Real-world SOC workflow simulation

# Skills Demonstrated

* Firewall deployment and configuration
* Network segmentation
* Traffic filtering
* Log analysis
* Basic incident response
* Understanding of SOC operations

# Lessons Learned

* Importance of firewall rules in securing networks
* How attackers generate detectable traffic
* Value of log monitoring in threat detection
* Practical understanding of network security
