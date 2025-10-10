---
title: Sub-domain Fuzzing
updated: 2023-07-25T13:04:55.0000000+01:00
created: 2023-07-25T12:37:15.0000000+01:00
date modified: Monday, May 13th 2024, 10:54:17 pm
---

A sub domain is any website underlying another domain. e.g. <https://photos.google.com> is the **photos** sub-domain of **google.com.** In this case we are checking different websites if they exist. In seclists, we can find popular subdomain wordlists.

1.  Short Scans: subdomains-top1million-5000.txt

For example:

*ffuf -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u <https://FUZZ.hackthebox.eu/>*

Gives us a few sub-domains:
![image1](../../../../_resources/image1-144.png)

We can then try running the same command on **academy.htb:**
![image2](../../../../_resources/image2-116.png)
No subdomains?

Even though we get no hits back, this doesn't mean there are no sub-domains. This means that are no **public subdomains under academy.htb** since it doesn't have a public DNS record. Since we only added the main domain in our **/etc/hosts** file our browser cannot locate other hidden sub-domains since we can only query the public DNS, which doesn’t have any domains.

