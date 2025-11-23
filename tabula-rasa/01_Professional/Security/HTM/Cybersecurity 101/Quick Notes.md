---
date created: Saturday, November 22nd 2025, 3:21:38 pm
date modified: Sunday, November 23rd 2025, 1:47:05 pm
---

# Quick Notes:

You've got a few specialised search engines:
- [Shodan](https://www.shodan.io/)
	- Searches the web for various types of servers, networking equipment, industrial control systems, different types/versions.
- [Censys](https://search.censys.io/)
	- Searches for internet-controlled hosts, websites, certificates, and other internet assets.
- [Virtus Total](https://www.virustotal.com/gui/)
	- Virus scanning service, by using multiple AV engines.
- [Have I been Pwned?](https://haveibeenpwned.com/)
	- Checks if an email address as appeared in a data-breach.

Vulnerabilities and Exploits:
- [CVE](https://www.cve.org/)
	- **Common Vulnerabilities and Exposures**, is a dictionary of all known vulnerabilities, it's maintained by MITRE.
- [Exploit Database](https://www.exploit-db.com/)
	- Contains exploit payloads to exploit systems based on various CVEs.

Social Media:
When conducting security incidents, use burner accounts.

Linux Fundamentals:

**Searching Commands:**
- `find -name *.txt*` - Searches for any .txt file
- `grep "81.143.211.90" access.log` - Searches the log file for any lines that have the corresponding IP.

**Shell Operators:**

| Symbol / Operator | Description                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| &                 | This operator allows you to run commands in the background of your terminal.                                                                     |
| &&                | This operator allows you to combine multiple commands together in one line of your terminal. (x && y, where y will only run if x succeeds)       |
| >                 | This operator is a redirector - meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere. |
| >>                | This operator does the same function of the `>` operator but appends the output rather than replacing (meaning nothing is overwritten).          |
