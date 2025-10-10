---
title: Active Subdomain Enumeration
updated: 2023-08-03T18:55:47.0000000+01:00
created: 2023-08-03T18:20:58.0000000+01:00
date modified: Monday, May 13th 2024, 10:19:31 pm
---

Introduction:

Now that we are able to actively enumerate the infrastructure, we will want to start looking at the DNS infrastructure of the company or the 3rd party DNS servers we have identified.

This is important because the amount of traffic generated **can lead to the detection of our reconnaissance activities.**

ZoneTransfers:

**Zone transfer** is how a secondary DNS server obtains info from a primary DNS server then updates it, this **master and slave** approach is used to organise DNS servers within a domain. The process is like so:

- The slaves receive updated DNS info from the master
- The master DNS is configured to enable **zone transfers** from the slave DNS servers.

We can use the service on [**hacker target**](https://hackertarget.com/zone-transfer/) to have an idea on what information we can gain from **zone transfers.** We can also us **dig** to perform this too.

A manual approach - CLI:

Firstly, we need to identify the name servers:
![image1](../../../../_resources/image1-155.png)

After this, we should use **nslookup** and query the following:
![image2](../../../../_resources/image2-126.png)

If we can perform a **zone transfer** we can **extract all the information from the domain**, we are looking for:
![image3](../../../../_resources/image3-97.png)

Inlanefreight:

HTB{h8973hrpiusnzjoie7zrou23i4zhmsxi8732zjso}
Fuzzing to reveal sub-domains:

In this example we are using **GoBuster**, but other fuzzing tools like ffuf would also work. Once we find patterns we can create our own **list of patterns** and use a wordlist from **seclists**. e.g. we find the pattern
**lert-api-shv-{NUMBER}-sin6.facebook.com.**

We then can construct a file that contains all the patterns we want to fuzz:
![image4](../../../../_resources/image4-76.png)

Then we can start GoBuster with the following flags:

**export TARGET="facebook.com"**
**export NS="d.ns.facebook.com"**
**export WORDLIST="numbers.txt"**
**gobuster dns -q -r "\${NS}"-d "\${TARGET}"-w "\${WORDLIST}"-p ./patterns.txt -o "gobuster\_\${TARGET}.txt"**

In which:
- **dns**
  - Launches the DNS module
- **-q**
  - quiet mode - doesn't print banner
- **-r**
  - Uses a custom DNS server
- **-d**
  - Target domain name
- **-p**
  - path to patterns file
- **-w**
  - path to wordlists file
- **-o**
  - save output to file.

Glossary:

- FQDN (Fully Qualified Domain Name)
  - This refers to the **absolute domain name** or the highest level domain/root.
