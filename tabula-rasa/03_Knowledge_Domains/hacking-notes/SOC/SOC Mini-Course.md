---
title: "Introduction to SOC:"
date modified: Wednesday, July 2nd 2025, 5:09:12 pm
youtube-link: https://www.youtube.com/watch?v=GxFBa-wfSbs
---

# Introduction to SOC:

A SOC (Security Operation Centre) is a central unit within an organisation which seeks to protect against cyber threats and seeks the uphold the **CIA triad (Confidentiality, Integrity and Accessibility).**

The main roles of someone working in a SOC is the following:
- Monitor and detecting any threats.
- Analysing data.
- Responding or Mitigating threats
	- This often depends on the maturity of the company and mostly their budget.

You can have a variety of SOC structures, each having their ups and downsides:
1. **In-house SOC**
	1. *This is a very expensive and rare form of security as the company has to front all the bills for staff, infrastructure, etc. But it is the most responsive and quick to dealing with threats and can be tailored to fit the organisation.*
2. **Outsourced SOC**
	1. *This is a cheaper alternative in which companies work with an MSSP (Managed Security Service Provider) that monitors many different companies at once. The benefit of this is that it is more economical, but may not full fit the needs of the client or have lightning fast response times for critical security incidents.*

SOCs typically operate on a **24/7 365 days a year.** This means that they always have somebody on shifts in order to ensure that the company/companies remain secure.

# Key Functions of a SOC:

The key responsibility of any SOC is to **monitor, detect and respond** to threats. This is achieved via working with **people, processes and technology** to harden defences.

The cycle of a SOC:
![[Pasted image 20240817161055.png]]

The building blocks of a SOC:
![[Pasted image 20240817161607.png]]
- People
	- *Refers to cyber-security specialists who can interpret data to understand what it means.*
- Process
	- *Refers to the procedures, protocols and steps that a SOC team will take when an issue occurs. Coming up with a playbook or a guide to when X or Y happens.*
- Technology
	- *Refers to the technology used to protect the systems in place.*
		- *SIEMs, IDS, Endpoint protection, etc*

**People and process** are perhaps more important than having every gleaming piece of new technology in place, since it will make the work more fulfilling, create a better environment and deliver better security.
***
# Roles Inside the SOC:

There are a few different key roles within any SOC, there are usually the following:

- **Tier 1 Analyst / (Junior) Security Analysts**
	- These team member usually focus on triaging events and escalating any serious threats, they are often the first points of contact in the SOC.
- **Tier 2 Analyst / Senior Security Analysts**
	- These team members usually focus on dealing with threats that have been escalated by junior analysts to understand the nature, scope and impact of the issues.
- **Tier 3 Analyst / Incident Response**
	- These team members are responsible for swift and effective response to any security breaches, lead efforts to contain, mitigate or stop threats. They often work with legal teams, law enforcement and/or media teams/human resources.
- **Threat Hunters**
	- These team members search for any avenues of risk within the organisation, they seek to improve threat detection capabilities within the SOC and try to identify holes in the SOC.
- **Threat Intelligence Analysts**
	- Collect, analyse and interpret data from various threat sources. They then share this information with the organisation to better protect against threats. The are a bit like the scouts or researchers of the team.
- **Security Engineers** 
	- Security Engineers develop and deploy secure systems to protect the organisation. Examples include firewalls, IDS (Intrusion Detection Systems), Endpoint protection, SIEMs, etc.
- **SOC Managers**
	- They oversee the processes of the SOC and work with other departments to ensure that things run smoothly.
***
# Tools in a SOC:

Many different types of tooling can be used within an organisation, but the most common tools are as followed:

- SIEM
	- Splunk
	- Microsoft Sentinel
- SOAR
	- Splunk Soar
	- Cortex
- EDR
	- CrowdStrike
	- Microsoft Defender
- WAF
	- Fortinet
	- Palo Alto
- IDS/IPS
	- Suricata/Snort
	- Zeek
- TIP
	- Recorded Future
	- Anomali

But remember that **A tool is just a tool.** One SIEM is going to be similar to another SIEM, so focus on learning the fundamentals of a SOC. Rather than obsessing over a single tool.

***
# Day in the file of a Tier 1 Analyst:

The cycle of a junior analyst is often as followed:
==Monitor -> Triage -> Escalate -> Recommendation==

## Monitor:
*You being with monitoring for alerts, this can be done via email, EDR or SIEMs or using a ticketing system.*
## Triage:
*You then need to determine if the alert is a false positive or a true positive.*
- **True positive**
	- The alert is a actual threat and has been recognised by the SIEM security tools in place.
- **False positive**
	- The alert is a false alarm and has been recognised incorrectly by the security tools in place.
## Escalate:
*If you have a problem, you should tell your client or a senior analyst and ask for help on how to remediate the issue.*
## Recommendation:
*If their is a false positive, talk with your client or security engineer and ask them to tune the SIEM.*

***
# Common Threats:

## Social Engineering:

Social engineering is once of the most pervasive attack vectors, it involves influencing somebody to steal sensitive data or manipulating somebody to perform a certain action.

This can be done in various methods
- Phishing - an email which seeks to manipulate a person into clicking a click, submitting a form or in any other method, gain sensitive information
- Spear Phishing - A phishing campaign in which the attack is personalised to the victim, often used when dealing with high-profile or highly-privileged people. 
- Vishing - A phone call pretending to be somebody important.
- Quishing - Phishing with a QR code.

## Identity Compromise:

Identity compromise is when an attacker uses information that they have gathered to gain unauthorized access to a users account to perform additional actions (a form of privilege escalation).

![[Pasted image 20240827163618.png]]

Lots of identity compromise occurs from the usage of one password for multiple accounts.

Using a password manager is a good way to prevent some of the low hanging fruit from effecting your company or organisation. 

## Malware:

Software that is designed to inflict damage to the users system or the organisation. There are many different types of malware.

![[Pasted image 20240827163841.png]]
***
# Frameworks and OSINT Tools:

We can use various frameworks in order to model and start performing SOC activities, some models are:

- NIST Incident Response Life-cycle
- SANS Incident Response Life-cycle
	- PICERL

How do we keep track of our attacker? - Again we have a few different models:
- The Lockheed Martin Kill Chain




