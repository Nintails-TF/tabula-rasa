---
date created: Sunday, December 28th 2025, 4:21:16 pm
date modified: Sunday, December 28th 2025, 5:52:38 pm
---

# SalineBreeze-1

## Challenge Description:
*Your manager has just informed you that, due to recent budget cuts, you'll need to take on additional responsibilities in threat analysis. As a junior threat intelligence analyst at a cybersecurity firm, you're now tasked with investigating a cyber espionage campaign linked to a group known as Salt Typhoon. Apparently, defending against sophisticated Nation-State cyber threats is now a "do more with less" kind of game.*

***Your Task:** Conduct comprehensive research on Salt Typhoon, focusing on their tactics, techniques, and procedures. Utilize the MITRE ATT&CK framework to map out their activities and provide actionable insights.*

*Your findings could play a pivotal role in fortifying our defences against this adversary. Dive deep into the data and show that even with a shoestring budget, you can outsmart the cyber baddies.*

## Challenge Deliverables:

### MITRE ATT&CK Framework (Tasks 1-8):

**Task 1:** Country attribution for Salt Typhoon - China
**Task 2:** Salt Typhoon active since - 2019
**Task 3:** Type of infrastructure targeted - ISPs/Networks
**Task 4:** Malware name associated with ID S1206 - Jumbled Path
**Task 5:** Operating system targeted by this malware - Linux
**Task 6:** Programming language of the malware - GO
**Task 7:** Vendor devices where malware acts as network sniffer - Cisco
**Task 8:** MITRE ATT&CK ID for Indicator Removal (log erasure) - T1070.002

***
## Picus Security Blog - December 20, 2024 (Tasks 9-11)

**Task 9:** CVE for Sophos Firewall vulnerability - **CVE-2022-3236**
**Task 10:** Registry key targeted for Crowdoor persistence - `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
**Task 11:** MITRE ATT&CK ID for registry modification technique - **MITRE T1112**

***
## TrendMicro Blog - November 25, 2024 (Tasks 12-15)

**Task 12:** Primary group name used in blog - **Earth Estries**
**Task 13:** Multi-modular backdoor using custom TLS-protected protocol - **GhostSpider**
**Task 14:** Full domain name with .dev TLD - `telcom.grishamarkovg8936.workers.dev`
**Task 15:** Filename for first GET request to C&C server - **Index.php**

***
## Securelist/Kaspersky Blog - September 30, 2021 (Tasks 16-20)

**Task 16:** Threat actor name at that time - **GhostEmperor**
**Task 17:** Malware name focus of article - **Demodex**
**Task 18:** Malware type - **Rootkit**
**Task 19:** Encryption type used in PowerShell dropper obfuscation - **AES**
**Task 20:** IOCTL code for hiding service from services.exe - **0x220300**

***

# Salt Typhoon Threat Intelligence Report:

[Salt Typhoon]([https://attack.mitre.org/groups/G1045/](https://attack.mitre.org/groups/G1045/)) is a People's Republic of China (PRC) state-backed actor that has been active since at least 2019 and responsible for numerous compromises of network infrastructure at major U.S. telecommunication and internet service providers (ISP).

The known malware they use is: [JumbledPath](https://attack.mitre.org/software/S1206/) it is a custom-built utility written in GO that has been used by [Salt Typhoon](https://attack.mitre.org/groups/G1045) since at least 2024 for packet capture on remote Cisco devices. [JumbledPath](https://attack.mitre.org/software/S1206) is compiled as an ELF binary using x86-64 architecture which makes it potentially useable across Linux operating systems and network devices from multiple vendors.

[Pictus Security](https://www.picussecurity.com/resource/blog/salt-typhoon-telecommunications-threat) has documented various CVEs associated with Salt Typhoon. Such as the [Sophos Firewall CVE (CVE-2022-3236)](https://nvd.nist.gov/vuln/detail/CVE-2022-3236). They have been evolving since inception.

They've been able to obtain persistence with a backdoor known as Crowdoor. [(Modify Registry - MITRE T1112)](https://attack.mitre.org/techniques/T1112/) 

[Trend Micro](https://www.trendmicro.com/en_us/research/24/k/earth-estries.html) also wrote a blog post detailing the acts of Salt Typhoon (Earth Estries). Additional malware was found - GHOSTSPIDER. It communicates with a C&C server using a custom protocol protected by TLS to ensure secure communication.

[SecureList](https://securelist.com/ghostemperor-from-proxylogon-to-kernel-mode/104407/) also referred to Salt Typhoon under the moniker of GhostEmperor in 2021. Analysing the demodex malware, a known rootkit. The Demodex malware was encrypted during runtime into AES.

SecureList


