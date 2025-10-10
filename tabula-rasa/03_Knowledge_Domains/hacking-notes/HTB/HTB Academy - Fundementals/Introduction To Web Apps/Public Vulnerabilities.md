---
title: 'Public Vulnerabilities:'
updated: 2023-07-18T23:20:24.0000000+01:00
created: 2023-07-18T20:55:52.0000000+01:00
---

Common Vulnerability Scoring System:

CVSS (Common Vulnerability Scoring System) is an industry standard for assessing the severity of security vulnerabilities. It provides severity score for vulnerabilities from 0 to 10. It helps with prioritization of resources and what to tackle first.

CVSS scores are based on a formula of several metrics:

- Base - is the score between 0-10
- Temporal - modifier that increases score.
- Environmental - modifier that increases score.

The **National Vulnerability Database** (NVD) provide CVSS for almost all known public vulnerabilities. The current scoring systems that are in place are CVSS v2 and CVSS v3. There are several difference between v2 and v3.

Namely the changes to base and **environment. (**<https://www.balbix.com/insights/cvss-v2-vs-cvss-v3/>)
![image1](../../../../_resources/image1-114.png)

Introduction:

The most important back-end component vulnerabilities are those that can be leveraged to take control of the whole back-end server without needing local access. Of which are normally caused by programming errors when building the back-end.

There is a wide range of vulnerabilities that can be exploited - from basic vulnerabilities that are easy to execute to very sophisticated bugs that require a deep knowledge.

Public CVE:

Public CVEs (Common Vulnerabilities and Exposures) are the first place to look when exploiting a system. Many open-source and proprietary applications get tested by experts and are assigned a CVE to record the bug and its impact.

Many of these penetration testers build **proof of concepts (POCs)** to show and test how a vulnerability can be exploited - these are often made public too so that others can use them for testing and research.

**The first step we want to take is to identify the version of software that is running -** we can look at GitHub repos for open source software or we can scan proprietary software, look at source code, etc.

Once we figure out the version of the web app we can google for exploits or look in databases:

- [Exploit DB](https://www.exploit-db.com/)
- [Rapid7 DB](https://www.rapid7.com/db/)
- [Vulnerabilty Lab DB](https://www.vulnerability-lab.com/)

We are generally interested in the CVEs that have the highest rating (8+) or **remote code execution** exploits. We can also look at exploits for plugins that the web app uses.

CVSS Guide:

<https://www.first.org/cvss/user-guide>

