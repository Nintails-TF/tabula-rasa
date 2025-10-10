---
title: Methodology
updated: 2023-08-15T15:06:32.0000000+01:00
created: 2023-08-14T18:22:05.0000000+01:00
date modified: Monday, May 13th 2024, 10:18:04 pm
---

Overview:

1.  Information Gathering
    1.  Collecting as much info about a target as possible.
    2.  OSINT and research
    3.  ***Before you even access the box/machine***
2.  Enumeration/Scanning
    1.  Running apps and scripts to check if servers are vulnerable.
3.  Exploitation
    1.  Use vulnerabilities on the system to get a foothold
4.  Privilege Escalation
    1.  Expand your access on the system.
    2.  Moving horizontally refers to accessing other users
    3.  Moving vertically refers to getting a higher permission group (root/admin/privileged user)
5.  Post-exploitation
    1.  Draft a final report - document your steps and how you would fix the problem (remediation).
Enumeration:

- [Attacking Web Apps with FFUF:](onenote:HTB%20Academy%20-%20Easy.one#Attacking%20Web%20Apps%20with%20FFUF&section-id={96CF2A91-65E4-4074-9AEE-EC63CF4F1EA7}&page-id={BD5627C7-A008-44F8-B72A-6AEABB97E1A4}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB)
  - URL Fuzzing
  - Recursive Fuzzing
  - Sub-domain Fuzzing
  - Virtual Hosts Fuzzing
  - Parameter Fuzzing (e.g. Cookies, PHP requests, etc.)
- [Web Requests:](onenote:HTB%20Academy%20-%20Fundementals.one#Web%20Requests&section-id={F1C3EE68-95D4-4786-A8FE-FBD2DA77AF8E}&page-id={C1B24E53-CB5D-41E5-B140-E75E262A4DC5}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB)
  - Looking at HTTP requests
  - Reading HTTP headers
  - Reading HTTP response codes
- [Using Web Proxies:](onenote:HTB%20Academy%20-%20Easy.one#Using%20Web%20Proxies&section-id={96CF2A91-65E4-4074-9AEE-EC63CF4F1EA7}&page-id={D08086F2-95D6-4912-BA24-BD7A69D22FB8}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB)
  - Intercepting requests
  - Repeating requests
  - Encoding and decoding requests/data
  - Using Proxies/proxychains to route our traffic.
  - Scanning websites using automatic BURP/ZAP scanners
- [JavaScript Deobfuscation](onenote:HTB%20Academy%20-%20Easy.one#JavaScript%20Deobfuscation&section-id={96CF2A91-65E4-4074-9AEE-EC63CF4F1EA7}&page-id={6DDABAAD-813A-4BFE-9458-35A91D5C637D}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB):
  - Beautifying code
  - Deobfuscating code
  - Analysing code.

Exploitation:

- [Hacking WordPress:](onenote:HTB%20Academy%20-%20Easy.one#Hacking%20WordPress&section-id={96CF2A91-65E4-4074-9AEE-EC63CF4F1EA7}&page-id={65B68627-1A50-4E87-BD96-DA6ABDA6B63F}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB)
  - Enumerating WordPress
  - Enumerating for vulnerable plugins/themes
  - Login brute forcing - via wp-login or via xmlrpc.php
  - Using metasploit with WordPress

- Metasploit
- Searching vulnerabilities online.

Privilege Escalation:

- LinPEAS and WinPEAS
- GTFO bins

Post-exploitation:

- 

Information Gathering:

- [Information Gathering - Websites:](onenote:HTB%20Academy%20-%20Easy.one#Information%20Gathering%20-%20Websites&section-id={96CF2A91-65E4-4074-9AEE-EC63CF4F1EA7}&page-id={7BDFE243-FA37-43F9-88D0-E5A9490AC1FE}&end&base-path=https://dmail-my.sharepoint.com/personal/2455717_dundee_ac_uk/Documents/infosecNotes/writeUps/HTB)
  - WHOIS and DNS records.
  - Passive and Active Subdomain enumeration.
  - Passive and Active infrastructure enumeration.
  - Virtual Host Fuzzing
  - Crawling
  - TLS and SSL certificates
  - **Whatweb, WafWoof, Aquatone**
- Google Searching
  - Searching up topics on google
  - Looking at guides/walkthroughs
    - **Don't use this to cheat your way through. Use it as a sanity check.**
  - Asking people for help.
  - Reading documentation.

