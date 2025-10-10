---
title: Stages of Pen tests
updated: 2022-10-19T19:23:09.0000000+01:00
created: 2022-10-19T19:03:16.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:10:57 pm
---

Generally penetration tests have the follow stages:

1.  Information Gathering
    1.  Collecting as much info about a target as possible.
    2.  OSINT and research
2.  Enumeration/Scanning
    1.  Running apps and scripts to check if servers are vulnerable.
3.  Exploitation
    1.  Use vulnerabilities on the system to get a foothold
4.  Privilege Escalation
    1.  Expand your access on the system.
    2.  Moving horizontally refers to accessing other users
    3.  Moving vertically refers to getting a higher permission group (root/admin/privileged user)
5.  Post-exploitation
    1.  Create a backdoor
    2.  Target other hosts
    3.  Gain sensitive information
    4.  Cover your tracks
    5.  Write a report

Types of pen tests:
![image1](../../_resources/image1-232.png)

Black-box testing is the slowest method of performing a pen test, but it mimics a real attack better and sharpens the skills of hackers the most.

Grey-box pen testing is popular, since you only get knowledge of some internal components or piece of software. It usually saves time, the logic is that since a black-box attacker will eventually get info about the system via scanning and enumeration, so we won't waste our time.

White-box testing is done by developers and ensure that every little detail is tested and coverred.
Existing Frameworks:

OSSTMM:

The OSSTMM manual has a long ass framework on testing and Cybersecurity: <https://www.isecom.org/OSSTMM.3.pdf>

The advantages of this book is that it is comprehensive and flexible to many use cases. The downside to this is that nobody will read this unless their money is on the line.

OWASP:

The OWASP is easy to pick up and understand and they regularly write reports on the top 10 security vulnerabilities. <https://owasp.org/>

The advantages of this is that it is easy to pick up and is technically literate and is frequently updated. The disadvantages are that it isn't accredited.

NIST Framework:

<https://www.nist.gov/cyberframework>

It is used in America and it is frequently updated, accredited. It has many good standards as well. The issue with it is that it doesn't talk about cloud computing and doesn't have good auditing policies.

NCSC CAF:

This is the UK's Cyber Assessment Framework. It is used as a framework for important services and activities like banking. It focusses on:

- Data security
- System Security
- Resiliency Monitoring
- Response and recovery.

It is government backed, but isn't used by lots of orgs and is based on principles rather than rules.

