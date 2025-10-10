---
title: Introduction to Researching
updated: 2022-10-20T14:58:32.0000000+01:00
created: 2022-10-19T19:23:36.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:10:24 pm
---

No hacker (professionals, amateur experienced or new) know everything. So when you encounter problems you don't know how to solve, you need to research.

## Approaching a foreign concept:

For example, you get an image from a CTF, you think there could be a flag inside of it, how do get that flag out of the image?

A seasoned hacker would know about stenography and be able to know a tool that could be used to check this image out. *But what if you don't even know what stenography is?*

First we can search:

- How to hide data inside an image.
  - From this we can learn what **Steganography** and by reading, we can figure out how files are hidden inside of an image.
- How to extract file from jpeg steganography?
  - We can then look at articles or links that describe how to actually use a steganography tool
  - For example Steghide could be used.

This is basically the process of learning most of everything, asking the right questions and reading information then applying it to a problem.

## Vulnerabilities Searching:

We frequently come across software that might be vulnerable to attack and exploitation. But how do we find these exploits?

We can use databases that track CVEs (Common Vulnerabilities Exposures) for all **public exploits**. These CVEs use the form

- ***CVE-YEAR-IDNUMBER***

Common websites include, ExploitDB, NVD and CVE Mitre. Though ExploitDB is helpful since you can download exploits right from the page, it is a good first stop.

You could also use searchsploit which allows you to search for exploits that have been downloaded from ExploitDB when creating Kali.

Importantly, CVE number are assigned when the vulnerability is discovered, not when they are published.)

I've found [CVE mitre](https://cve.mitre.org/index.html) to be a good tool.
