---
title: Perfection
date modified: Tuesday, May 14th 2024, 9:09:30 pm
---

## Enumeration:

```Bash
nmap 10.10.11.253 -sC -sV -oN perfection-scan
...SNIP...
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 80:e4:79:e8:59:28:df:95:2d:ad:57:4a:46:04:ea:70 (ECDSA)
|_  256 e9:ea:0c:1d:86:13:ed:95:a9:d0:0b:c8:22:e4:cf:e9 (ED25519)
80/tcp open  http    nginx
|_http-title: Weighted Grade Calculator
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

We have two open ports, SSH and HTTP. The website seems to be a calculator of some kind.
![[Pasted image 20240514200702.png]]

Looking around the website we can see the following:
- The website is powered by **WEBrick 1.7.0** 
	- This software could be unpatched.
		- Metasploit reveals that you can DOS this version of WeBirck. But that doesn't help us gain access.
- The web server that is running is **nginx** with Ruby 3.0.2
	- The doubletap exploit appears to enable RCE for this version of Ruby, but we need to find where the rails.root info is stored.
- The calculator page acts as a form in which we can send data through.
	- Could be vulnerable to XSS.

**Fuzzing:**

Fuzzing attempts doesn't give any new web pages 
```Bash
ffuf -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -u http://10.10.11.253/FUZZ  
```

**XSS:**

Trying to perform an XSS attack using the payload:
```Bash
<img src=x onerror=alert('XSS');>
```

Leads to the following page being generated:
![[Pasted image 20240514205218.png]]
We have methods to bypass this kind of templating on ruby using: https://book.hacktricks.xyz/pentesting-web/ssti-server-side-template-injection#erb-ruby

I refreshed the page and landed on:
![[Pasted image 20240514205245.png]]

I assume we need to inject these commands into the webpage, we would use "Hello World". There also is a file that points to:
```URL
http://10.10.11.253/__sinatra__/404.png
```
Which shows us an image of a microphone. This image could have something inside of it?

Using tools like **binwalk, exiftool and steghide** don't appear to reveal anything.
## Exploitation:

## Foothold:

## Privilege Escalation:

## Lessons Learned

