---
date created: Saturday, October 11th 2025, 9:57:46 am
date modified: Saturday, October 11th 2025, 10:07:28 am
---

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


