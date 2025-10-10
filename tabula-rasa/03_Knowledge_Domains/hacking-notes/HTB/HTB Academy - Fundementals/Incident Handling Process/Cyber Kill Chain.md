---
title: Cyber Kill Chain
date modified: Sunday, May 26th 2024, 2:05:44 pm
---
## What is the Cyber Kill Chain?:

Before we begin to talk and handle incidents, we will want to understand the **cyber kill chain**(the attack lifestyle). This will provide us insight on how far in the network or system that an attacker is and what they may have permissions for.

This is key during the investigation phase, as it allows us to assess the damage that has been done.

The cyber kill chain has 7 different stages:
![[Pasted image 20240519143300.png]]
## Recon:

*The recon phase is when the attacker looks for and then chooses their target. After deciding on a target, an attacker will want to gather as much useful information as possible.*

Some attackers use passive information gathering, which uses attack vectors such as:
- Gathering details from social media
	- LinkedIn, Instagram, YouTube, Twitter, etc.
- Looking at documentation on the targets web pages
	- **Website Content -** About us pages, press releases, job postings, articles and blogs.
	- **Technical Documentation** - API documentation, Product manuals, user guides.
	- **Legal Documentation** - SEC Filings (public companies), compliance reports, government and regulation reports.
	- **Domain and network information -** WHOIS records, DNS records, SSL/TLS certificates.
- Looking at vendors and partner details
	- Look at info about products that the target uses.
	- Look into partner collaborations and integrations with other companies.
- Analysing historical data
	- Viewing cached web pages.
	- Looking at old data breaches / leaked documents.
- Google Dorking

Attackers can use more active methods such as:
- Scanning ports
- Network scanning
- Vulnerability scanning
- Banner grabbing
- Web app testing
- Social engineering
- Wireless network attacks
- Password attacks
- Phishing Campaigns
- DNS interrogation
- Packet sniffing
## Weaponize:

*The weaponization phase involves using malware to gain initial access, this malware is embedded into an exploit or payload. This malware is very lightweight and undetectable by AV and detection tools.*

Attackers also try to gather details on the AV (Anti-virus) or EDR (Endpoint Detection and Response) systems that are in place.

Attackers ultimately want to gain remote access via a compromised machine, in which they have persistent access through machine reboots and the ability to transfer any tools and programs they may need.
## Delivery:

*In the delivery phase, the exploit or payload has reached the victim(s). The most traditional approaches are: **Phishing emails -** either containing a malicious link or attachment.*

A web page can either contain an exploit that infects the system of the victim or host a malicious payload that attacks the victims system.

Another clever tactic is impersonation a legitimate log-in form and harvesting and credentials that are entered. Social engineering is also another pervasive and effective tactic, in which a victim is persuaded into running a payload.

These payloads are stored on attacker controlled websites that mirrors a well-known website to the victim - *Think of a clone of a target organizations website.* Payloads are almost always simple to execute, having no more than a double click on a file or script.

Finally, physical methods can be used to deliver payloads, like scattering USB drives around an area - hoping that somebody plugs them into a computer.

## Exploitation:

*In the exploitation phase, is when the bomb goes off - the exploit is triggered on the machine/system and is compromised. Such exploits include - but are not limited to:*

- Exploit scripts
	- metasploit payloads, etc.

## Installation:

The installation phase occurs after the exploit has been executed and is running on the compromised machine. Now the attacker is free to do what they want, which may differ depending on their intentions, but common techniques are:

- Dropper
	- Droppers are small pieces of code that are design to install malware and tools on a target system.
	- Droppers frequently use obfuscation to prevent detection of any malicious code.
- Backdoor
	- A backdoor is malware that provides an attacker with ongoing access to the system.
	- A backdoor can be installed in the exploitation phase or placed on the compromised system with a dropper.
	- Backdoor enables attackers to launch new attacks and steal information from the target system.
- Rootkits
	- Rootkits are stealthy pieces of malware that are planted into compromised systems with the goal of remaining hidden from AV and other detection mechanisms.
	- Rootkits can escalate privileges and provide attackers with more control over the system.

***
## Command And Control:

*During the command and control phase, the attack will establish a remote access capabilities on the infected machine. There are various ways of achieving this:*

1. Running a modular initialiser that loads scripts and commands when needed.
2. Using scripts to replicate multiple variants of malware across the network to infect more machines
	1. This is a more advanced method and it used by attackers to ensure they have backup devices if they get discovered and contained. 
	2. This replication means that they can return to the environment and continue to deal damage.

***
## Action:

This is the final stage of the cyber kill chain, in which adversaries can move to more and more systems, or can exfiltrating data or deploy ransomware.

Finally, do note that these **steps aren't always linear.** Previous phases of the cyber kill chain can be looped to identify more targets to exploit and further enumerate and dig into the network.

**Our main goal is to stop attackers from progressing further up the kill chain.** We want to keep them stuck in the earlier stages.
***
## Recap:

- The cyber kill chain has 8 distinct stages:
	- ***Recon, Weaponization, Delivery, Exploitation, Installation, C&C and Action.***
	- Our job as incident handling is to figure out which stage an adversary is at, then to push them back or slow them down.
- Recon
	- Attackers seek to gather as much useful information as possible. This can be done an an passive or active way.
- Weaponization
	- Attackers design light-weight malware to gain access to remote machines, ideally with some kind of persistence between reboots.
- Delivery
	- Attackers deliver malware or exploits to systems, frequently this is done via social engineering based attacks like phishing.
- Exploitation
	- Attackers activate the malware and take over the infected systems.
- Installation
	- Attackers embed themselves deeper into the systems, via tools like droppers, backdoors and rootkits.
- Command and control
	- Attackers achieve remote access on the infected machines/networks. Often during this stage, attackers try and map out the network and further spread malware to compromise more systems.
- Action
	- Attackers are finally able to achieve their mission. This can be exfiltrating valuable data or deploying ransomware.


