---
title: "Introduction:"
date modified: Sunday, May 26th 2024, 2:33:56 pm
---
# Introduction:

In the **preparation** stage we have two separate objectives:

1. *Establishing the incident handling capability within the organisation.*
	1. You can think of this as getting the scaffolding in place to start a building.
2. *Having the ability to implement protective measures against possible security incidents.*
	1. This can include: *endpoint and server hardening, active directory tiering, multi-factor authentication (MFA), privileged access management, and so on.*
	2. You can think of this as building walls and defences to prevent attackers from progressing in the cyber kill chain.

Security teams are not totally responsible for any and all security incidents, because preparing for security incidents is a job for the whole team.

***
## Preparation Prerequisites:

During the preparation phase, we need to ensure that we have the following resources:
- *Skilled incident handling team members (We can outsource/contract the heavy lifting to a SOC Provider or MSP/MSSP), but we want our team to have at least a basic understanding of security incident handling.*
	- e.g. We want our team to be able to do basic preparation and monitoring activities, then escalate to those who are more knowledgeable when needed.
- *A Trained workforce (as much as possible, using security awareness activities or training.)*
	- We want to minimize the impact of phishing and other forms of social engineering attacks.
- Clear policies and documentation.
	- We need to have step-by-step guides in place for when fires are started.
- Tools
	- SIEMs, EDRs, IDSs, etc.

***
## Clear Policies and Documentation:

We will want to have up to date information on the following policies and documentation:

- *Contact information and roles in the incident handling process*
	- Make sure we can contact everyone on the team quickly·
- *Contacting for the legal and compliance department, management, IT support, media relations, LE, ISPs, facility management and external incident response team.*
	- Make sure we can contact other parties that will be affected by the incident.
- *Incident response policy, plan and procedures.*
- *Incident information sharing policy and procedures.*
- *Baselines of systems and networks from a clean state environment.*
	- So we are aware of what the normal operations look like, so we can see if anything is amiss by looking at a snapshot of what is normal.
- *Network diagrams*
	- So that we can navigate the network easily and understand which areas to look in.
- *Organization-wide asset management database.*
	- Checking everything we have access to for anything fishy.
- *User accounts with excessive privileges that can be used on-demand by the team to quickly fix problems.*
	- *This includes business critical systems, which the skills are needed to admin said system.*
	- *These user accounts are enabled when an incident is confirmed during an investigation and are disable when it is over. A password reset is also performed when disabling the users.*
- *Ability to acquire hardware, software or external resources quickly.*
	- *You need a budget to buy a tools quickly, you don't want to wait weeks for the approval of a $500 tool.*
- *Forensic/Investigative cheat sheets.*
	- Aiding in the speed of solving problems.
***
## Dealing with incidents:

Non-severe cases can often be handled quickly and without too much friction in the organisation or with partners. In other cases, you may need to contact LE and communicate with customers and third-party vendors, especially when legal concerns arise.

For example:
*A data breach that involves customer data has to be reported to LE within a certain time frame in accordance to GDPR. There also may be additional compliance steps required depending on the location and/or branches where the incident has occurred.*

This is why it is important to have a strong link to your **GRC (Governance, Regulation and Compliance)** team.

Documentation is vital, but you must document the event as it is happening, so you need to establish an **effective reporting mechanism**. Incidents can be very stressful and it is easy to forget parts of it, especially when people are working fast to fix problems.

Try to remain calm, take notes and ensure that these notes contain timestamps, the activity performed, the result of it and who did it. 

**We want to figure out the answer to who, what, when, where, why and how.**
***
## Tools (Software and hardware)

Moving forward, we also need to ensure that we have the right tools for the job, these include but are not limited to:

- Additional laptop or forensic workstation, this is required for each incident handling team member for various activities such as:
	- Preserving disk images and log files
	- Performing data analysis
	- Investigating without restriction
		- These laptops will test malware so AV should be disabled, these devices must be handled in a safe way when conducting this though.
- Digital forensics images acquisition and analysis tools
- Memory capture and analysis tools
- Live response capture and analysis
- Log analysis tools
- Network capture and analysis tools
- Network cables and switches
- Write blockers
- Hard drives for forensic imaging
- Power cables
- Screwdrivers, tweezers and any other tools to disassemble/fix hardware if needed.
- Indicator of Compromise (IOC) creator and the ability to search for IOCs across the organisation's network.
- Chain of custody forms
- Encryption software
- Ticket tracking system
- Secure facility for storage and investigation
- Incident handling system independent of your organisations infrastructure.

All or some of these tools can be combined into a **jump bag.** Which can be picked up quickly on the fly if an incident every happens so that you can respond as quickly as possible.

**Most importantly,** you need to have your documentation system be **completely independent** of your companies infrastructure. Because the attackers may still have access to your whole domain. You want to assume that adversaries have control over everything.

*You don't want adversaries listening into and reading communication.*
***
## Protective Measures:

Another part of the **preparation phase** is to protect proactively against any incidents. An incident handling team should be aware about any protection related activities, so that they know where to go to look for evidence/artifacts.

Highly recommended protective measures include:
- DMARC
- Endpoint Hardening & EDR
- Network Protection
- Privilege Identity Management / MFA / Passwords
- Vulnerability Scanning
- User Awareness Training
- Active Directory Security Assessment
- Purple Team Exercises

### DMARC:
[DMARC](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-dmarc) (Domain-based Message Authentication Reporting and Conformance) is email protection that is built upon existing [**SPF](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-spf) (Sender Policy Framework) and [DKIM](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-dkim)(Domain Keys Identified Mail).** 

DMARC will reject emails that **pretend** to originate from your organisation. This means, if an adversary is spoofing an email pretending to be an employee asking for an invoice to be paid, the system will automatically block the email before it is reaches the recipient.

DMARC is easy and inexpensive to implement, but requires lots of testing; otherwise you can block legitimate emails and be unable to recover them.

### Endpoint Hardening and EDR:
Endpoint devices (workstations, laptops, etc.) are entry points for most attacks that we end up facing on a daily basis. Most threats originate from the internet and will target users that are browsing websites, opening attachments or running malicious executable. A percentage of this activity will be from corporate endpoints.

There are a few recognized endpoint hardening standards, with the CIS and Microsoft standards being most popular, these are often the building blocks for your organisations hardening baselines, highly important actions that work include:

- *Disabling LLMNR/NetBIOS*
- *Implement LAPS and remove admin privileges from regular users.*
- *Disable or configure PowerShell in `ContrictedLanguage` mode.*
- *Enable Attack Surface Reduction (ASR) rules if using Microsoft Defender.*
- *Implement whitelisting. This is nearly impossible to implement. But Consider at least blocking execution from user-writable folders (Downloads, Desktop, AppData, etc)*
	- Block scripts such as `.hta, .bat, .vbs, .cmd, js, etc.`
	- Look at [LOLbins](https://lolbas-project.github.io) files when implementing whitelisting, as these vectors are used when gaining initial access to bypass whitelisting.
- Use host-based firewalls. At a bare-minimum, block workstation to workstation communication and block outward traffic to LOLBins.
- Deploy EDR product. 
	- [AMSI](https://learn.microsoft.com/en-us/windows/win32/amsi/how-amsi-helps) provides create help into obfuscated scripts for anti-malware products to inspect content before it gets executed.
	- Only choose to use products that integrate with your AMSI or EDR product.

The key rule when performing endpoint hardening is, **don't let perfect be the enemy of good.**

### Network Protection:
Segmenting your networks is a powerful technique that prevents breaches from spreading across the whole organization. Business-critical systems must be isolated and only accept communication when required.

Critical infrastructure should also not be internet facing unless placed into a DMZ.

IDS and IPS systems are important to consider. They can help when SSL/TLS interception is performed to identify malicious traffic based on content, rather than by IP reputation.

It is also important to ensure that organization improved devices can gain access to the network. Solutions such as 802.1x can reduce the risk of BYOD devices connecting to a corporate network.

On the cloud, you can use tools like Azure/Azure AD with Conditional Access policies to access organization resource only if you are connecting from a company managed device.

### Privilege Identity Management / MFA / Passwords:

Currently, stealing privileged user accounts is the most common escalation path in Active Directory (AD) environments.

Admin users often either have a weak (but complex) password or a shared password with their regular user account (which could be obtained by many attack vectors like keylogging).

For reference a passwords can be constructed in various ways:
- Weak, low complexity password.
	- admin
- Weak, but complex password
	- Password1!
- Strong, complex password
	- 1Dr43m0fthermintr33s?d0y0u!

It is a good idea to use passphrases rather than passwords (1LiK3myC0FFe3Warm). Combining words from a 2nd language is also a good idea.

MFA is another identify-protection solution that should be implemented at LEAST for any admin access to **ALL** applications and devices.

### Vulnerability Scanning:
Performing continuous vulnerability scans of your environment and remediate all of the high and critical vulnerabilities that are discovered. Whilst scanning is often automated, fixing usually requires manually tinkering with things, If you can't apply patches, then segment the systems that are vulnerable.

### User awareness training:
Training users to recognise suspicious behaviour and report it when discovered is a big win for us. We will never reach 100% coverage in our team, but training our team results in less compromise via phishing.

Surprise testing should be done as part of this training, e.g. monthly phishing emails, dropped USB sticks, etc.

### Active Directory Security Assessment:
The best way to find misconfigurations or exposed critical vulnerabilities in AD is to look at them from the perspective of an attacker. Doing your own reviews or getting a third party to do so will ensure that when an endpoint device is compromised, that the attacker will not have one-step escalation to higher level privileges.

The more tools that an attacker tries to use, the higher likelihood that your automated systems will detect one of these methods. So we want to eliminate low hanging fruit and easy wins as much as possible.

### Purple Team Exercises:
We need to train our security team and keep them vigilant. We can do this via purple teaming. In which a red team continuously or eventually inform the blue team about their actions, findings, any security shortcomings, etc.

This helps the blue team know where to divert their attention to when fixing problems or hardening the system. If a threat is missed, their is an opportunity to improve. If a threat is detected, the blue team can test any playbooks from their incident handling procedures to check if they work and prevent the attack.

It is a win-win either way.
***
## Recap:

- The preparation phase is all about two main objectives
	1) Making sure your organisation has the ability to handle security incidents.
	2) Having the ability to implement protective measures against potential threats.

- The **resources that we need** to prepare correctly are:
	- Skilled incident handling team members
		- If we don't have these we need to outsource the heavy lifting to a trusted 3rd party.
		- We need an in-house team which can perform basic activities of security handling.
	- A trained workforce.
		- Since social engineering is a huge threat, we want to ensure that our team has some knowledge about these methods of attack.
	- Clear polices and documentation
		- Since things get very hectic during security incidents, having strict rules and guidelines help a lot.
		- It also ensures that we follow the correct laws and regulations.
	- Defensive tools
		- SIEMs, EDRs, IDSs, etc.

- We want to have the following articles of policies and documentation:
	- Important contact info
		- Key team members, compliance,  management, IT support, media relations, etc.
		- LE, ISPs, external incident response team - if applicable.
	- Policy, plan and procedures for the IR team.
	- Information sharing policy.
	- Baselines of systems and networks from a clean state environment.
	- Network diagrams.
	- Organization wide asset management database.
	- User accounts that have high privilege to quickly fix problems.
	- A war budget to quickly purchase essentials.
	- Forensic/Investigative cheat sheets/resources.

- Non-severe cases can be handled quickly without much friction in the organisation.
- Severe cases might need to be raised to your GRC team or LE.
- You need to have effective reporting to record everything that happens during a security incident.
	- This ensures that people don't forget or overlook certain features and helps create a timeline.

- It is a great idea to have a **jump bag** filled with tools to go when shit hits the fan. Good items to include are:
	- An additional laptop
	- Digital forensics image acquisition and analysis tools
	- Memory capture and analysis tools
	- Live response capture and analysis tools
	- Network capture and analysis tools
	- Write blockers
	- Hard drives
	- Power cables
	- Screwdrivers, tweezers and any other tools to disassemble/fix hardware if needed.
	- IOCs
	- Chain of custody forms
	- Encryption software
	- Ticket tracking system
	- Secure facility for storage and investigation
	- Incident handling system independent of your organisations infrastructure.


- We can implement the following features to protect our organisation more.
	- **Always remember that perfect is the enemy of good.** So don't beat yourself up if everything isn't perfect.
		- DMARC
		- EDR and endpoint hardening
		- Network restrictions and hardening
		- Strong passwords and MFA.
		- Vulnerability Scanning
		- User awareness training
		- Active directory security assessments.
		- Purple team exercises

***

