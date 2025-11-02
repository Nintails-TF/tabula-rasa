---
date created: Saturday, October 11th 2025, 10:17:46 am
date modified: Wednesday, October 15th 2025, 11:59:58 am
---

# CDSA Academy Modules

### Incident Response & Forensics
- [Incident Handling Process](./Academy%20Modules/Incident%20handling%20Process.md)
- [Introduction to Digital Forensics](./Academy%20Modules/Introduction%20to%20Digital%20Forensics.md)
- [Security Incident Reporting](./Academy%20Modules/Security%20Incident%20Reporting.md)

### SIEM & Log Analysis
- [Security Monitoring and SIEM Fundamentals](./Academy%20Modules/Security%20monitoring%20and%20SIEM%20Fundamentals.md)
	- *Estimated: 5 hours*
	- *Actual: 1.5 hours*
- [Understanding Log Sources & Investigating with Splunk](./Academy%20Modules/Understanding%20Log%20Sources%20%26%20Investigating%20with%20Splunk.md)
- [Detecting Windows Attacks with Splunk](./Academy%20Modules/Detecting%20Windows%20Attacks%20with%20Splunk.md)

### Threat Detection & Hunting
- [Introduction to Threat Hunting and Hunting with Elastic](./Academy%20Modules/Introduction%20to%20Threat%20Hunting%20and%20Hunting%20with%20Elastic.md)
- [YARA & Sigma for SOC Analysts](./Academy%20Modules/YARA%20%26%20Sigma%20for%20SOC%20Analysts.md)

### Windows Security
- [Windows Event Logs & Finding Evil](./Academy%20Modules/Windows%20Event%20Logs%20%26%20Finding%20Evil.md)
- [Windows Attacks & Defence](./Academy%20Modules/Windows%20Attacks%20%26%20Defence.md)

### Network Analysis
- [Into to Network Traffic Analysis](./Academy%20Modules/Into%20to%20Network%20Traffic%20Analysis.md)
- [Intermediate Network Traffic Analysis](./Academy%20Modules/Intermediate%20Network%20Traffic%20Analysis.md)
- [Working with IDS & IPS](./Academy%20Modules/Working%20with%20IDS%20%26%20IPS.md)

### Malware Analysis
- [Introduction to Malware Analysis](./Academy%20Modules/Introduction%20to%20Malware%20Analysis.md)
- [JavaScript Deobfuscation](./Academy%20Modules/JavaScript%20Deobfuscation.md)
***
# Learning Outcomes

## Key Skills:

- **SIEM Tools**: Practical experience with Elastic Stack and Splunk
- **Threat Detection**: Creating detection rules and queries
- **Digital Forensics**: Memory and disk analysis, timeline construction
- **Log Analysis**: Windows Event Logs, Sysmon, network traffic
- **Threat Intelligence**: Interpreting CTI reports and applying them operationally
- **Incident Response**: Full lifecycle from detection to reporting
- **Security Monitoring**: Real-time monitoring and alert triage

## Tools:

- **SIEM & Security Monitoring Tools**
    - **Splunk** - Enterprise SIEM platform for log aggregation, analysis, and creating detection searches using SPL (Search Processing Language)
    - **Elastic Stack (ELK)** - Open-source SIEM solution including Elasticsearch, Logstash, and Kibana for log analysis and threat hunting using KQL
- **Digital Forensics & Incident Response (DFIR) Tools**
    - **FTK Imager** - Forensic imaging tool for acquiring disk images and preserving digital evidence
    - **KAPE** (Kroll Artifact Parser and Extractor) - Rapid triage tool for collecting and parsing Windows artifacts
    - **Velociraptor** - Advanced open-source endpoint monitoring and digital forensic platform for incident response
    - **Volatility** - Memory forensics framework for analysing RAM dumps and investigating malicious activity in memory
- **Network Traffic Analysis Tools**
    - **Wireshark** - Network protocol analyser for deep packet inspection and traffic analysis
    - **Tcpdump** - Command-line packet capture tool for network traffic monitoring
    - **Zeek** (formerly Bro) - Network security monitoring framework that logs and analyses network traffic
- **IDS/IPS & Network Monitoring**
    - **Suricata** - High-performance network intrusion detection and prevention system
    - **Snort** - Open-source intrusion detection and prevention system for real-time traffic analysis
    - **Zeek** - Also functions as a network security monitor (listed above under network analysis)
- **Detection & Threat Hunting Tools**
    - **YARA** - Pattern matching tool for creating custom malware detection rules
    - **Sigma** - Generic signature format for SIEM systems, enabling portable detection rules
    - **Sigmac** - Converter tool for translating Sigma rules into SIEM-specific queries
    - **Chainsaw** - Windows event log forensics tool for rapid threat hunting and analysis
- **Windows Security & Monitoring Tools**
    - **Sysmon** - Windows system monitoring tool that logs detailed system activity to Event Logs
    - **Event Viewer** - Native Windows application for viewing and analysing Windows Event Logs
    - **Get-WinEvent** - PowerShell cmdlet for querying and filtering Windows Event Logs
    - **ETW** (Event Tracing for Windows) - Low-level Windows tracing framework for detailed system monitoring
- **Forensic Artifacts & Analysis**
    - **MFT** (Master File Table) - NTFS file system structure used for timeline reconstruction
    - **USN Journal** - NTFS change journal for tracking file system modifications
    - **Registry Hives** - Windows registry analysis for artifact extraction
    - **Prefetch Files** - Windows files showing application execution history
    - **ShimCache** - Windows application compatibility cache for execution tracking
    - **Amcache** - Windows artifact tracking program executions and installations
    - **BAM/DAM** (Background Activity Moderator) - Windows artifact for tracking application execution times
    - **SRUM** (System Resource Usage Monitor) - Windows database tracking application and network usage

***