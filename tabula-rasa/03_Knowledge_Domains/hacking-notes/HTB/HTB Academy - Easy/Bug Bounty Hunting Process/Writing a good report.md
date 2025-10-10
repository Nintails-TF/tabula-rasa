---
title: 'Writing a good report:'
updated: 2023-02-01T07:36:06.0000000+00:00
created: 2023-01-30T10:31:55.0000000+00:00
---

Using a CVSS Calculator:

Describing the base score of the CVSS calculator consists of the:

1.  *Attack Vector - Refers to how the vulnerability can be exploited*
    1.  ***Network (N):** Attackers can only exploit this via the network layer (remotely exploitable).*
    2.  ***Adjacent (A):** Attackers can only exploit this only if they are on the same logical or physical network, this includes secure VPN connections.*
    3.  ***Local (L):** Attackers can only exploit this via accessing the system locally, or remotely using SSH, or via user interaction.*
    4.  ***Physical (P):** Attackers can exploit this vulnerability through physical interaction and manipulation, like playing a sound to crash your computer.*

2.  *Attack Complexity - Depicts the conditions beyond the attackers control and must be present to exploit the vulnerability.*
    1.  ***Low (L):** No special preparations should take place to exploit the vulnerability successfully. The attackers can exploit the vulnerability successfully repeatedly without any issues.*
    2.  ***High (H):** Special preparations and information gathering should take place beforehand to exploit the vulnerability successfully.*

3.  *Privileges Required - Show*s the level of privilege that the attacker must have.
    1.  ***None (N):** No special access relating to settings or files is required to exploit the vulnerability successfully, an unauthorized perspective can use the exploit.*
    2.  ***Low (L):** The attacker should possess standard user privileges to perform the exploit. The exploitation in this case affects files and settings owned by a user or non-sensitive assets.*
    3.  ***High (H):** Attackers should possess admin or root level privileges, The exploit in this case affects the whole system usually.*

4.  *User Interaction - Shows if attackers can use the exploit on their own or if users need to do something.*
    1.  ***None (N):** Attackers can use the exploit independently of users.*
    2.  ***Required (R):** A user needs to take an action before the attacker can exploit the vulnerability.*

5.  *Scope - Shows if successful exploitation of the vulnerability can affect other components in the system.*
    1.  ***Unchanged (U):** Successful exploitation of the vulnerability affect the vulnerable component or resource managed by the same component.*
    2.  ***Changed (C):** Successful exploitation of the vulnerability affects components beyond the scope of the components security authority.*

6.  *Confidentiality - Shows how much sensitive information is disclosed.*
    1.  ***None (N):** The confidentiality is unimpacted.*
    2.  ***Low (L):** The vulnerable component will experience some loss, attackers can gain access to some restricted information but cannot search over what info is obtained.*
    3.  ***High (H):** The vulnerable component results in a total or serious loss, attackers can access to all or some control over information.*

7.  *Integrity - Shows how much data can be modified or altered.*
    1.  ***None (N):** The integrity of the vulnerable component does not get impacted.*
    2.  ***Low (L):** Attackers can modify data in a limited manner, Attackers don't have control over the consequence of a modification and the component isn't seriously affected in this case.*
    3.  ***High (H):** Attackers can modify all critical data on the component. Attackers have control over the consequence of a modification and the vulnerable component will experience a total loss of integrity.*

8.  *Availability - Shows how much the performance of the system gets impacted.*
    1.  ***None (N):** The availability of the vulnerable component does not get impacted.*
    2.  ***Low (L):** The vulnerable component results in some loss of availability. The attacker does not have complete control over the vulnerable component's availability and cannot deny service to users. Performance is reduced.*
    3.  ***High (H):** The vulnerable component results in severe or total loss of service. Attackers can control the availability of a component and can deny users. Performance is significantly reduced.*

Introduction:

By documenting our findings clearly and concisely, we can get straight to the point for the security and triage team. The most important feature of a bug bounty report is how each **vulnerability can be reproduced**.

It may be necessary to translate technical security issues into more understandable/business terms to understand the impact of each vulnerability.

The essential elements of a good bug report are:
- **Vulnerability Title**
  - *We need to include vulnerability type, affected domain/parameter/endpoint, impact.*
- **CWS/CVSS score**
  - *For communicating the nature and severity of the vulnerability.*
- **Vulnerability Description**
  - *Explaining the vulnerability in greater detail.*
- **Proof Of Concept**
  - *Steps to reproduce the vulnerability clearly and concisely.*
- **Impact**
  - *Elaborate on what a bad actor can do by exploiting the vulnerability. Business impact and max damage should be included in the impact statement.*
- **Remediation**
  - *This is optional, but this can be a suggestion on how to fix/mitigate the issue.*

CWE and CVSS:

MITRE describes the [**Common Weaknesses Enumeration** (CWE)](https://cwe.mitre.org/data/definitions/1387.html) as a community-developed list of software and hardware weakness types. It serves as a common language and acts as a measuring stick for security tools. You use it to categorise the vulnerability you are exploiting.

If you are using a **chain** of vulnerabilities, you should start with a CWE that relates to the initial vulnerability.

To communicate the severity of vulnerabilities, we can use the [**Common Vulnerability Scoring System** (CVSS)](https://www.first.org/cvss/), system to get a number that can relate to how critical our vulnerability is.

Example report:
![image1](:/5297eb08a4ee4fb58b33ca410ca2900f)

![image2](../../../../_resources/image2-94.png)
