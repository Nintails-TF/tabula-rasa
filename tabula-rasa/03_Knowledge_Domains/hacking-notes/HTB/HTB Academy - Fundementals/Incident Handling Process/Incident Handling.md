---
title: "Incident Handling's Value and Generic Notes"
date modified: Sunday, May 26th 2024, 1:20:05 pm
---
## Introduction:

**Incident handling** is an important tool for organisations and companies to combat security problems. Whilst protective measures are always being updated and improved, there is a need to have a human monitoring the system in order to prevent compromise.

Certain organisations often value confidentiality, Integrity and availability of data (CIA triad). 
Such institutions include:

- **Finance and Banking**
	- JP Morgan, TSB, etc.
		- These institutions include personal and financial details about their customers. If they are breached, this can result in fraud and the loss of trust and client's money.
- **Technology Companies**
	- Google, Microsoft
		- These companies run many different services and platforms. If users data is compromised or their networks/services are brought down, they lose money and confidence.
- **Retail and E-commerce**
	- Amazon, Any online shop (e.g. M&S), Patreon
		- These companies hold payment details and make money via an online store, so if their service is brought down they lose money.
- **Telecommunications**
	- BT, EE, etc
		- If these companies are compromised or their services are rendered unavailable, they will have lots of angry customers, who don't have internet/mobile data.
- **Energy and Utilities**
	- Scottish power, BP, etc.
		- An attacker could mess with powerplant controls, water systems, etc. Of which would be a massive problem if occurred.
- **Healthcare**
	- NHS, Boots, etc.
		- Having medical data stolen or services degraded could result in people dying or becoming sicker, not a good thing if it happens.
- **Manufacturing**
	- Rolls-Royce, BAE systems
		- Automated system can be compromised or designs of products can be leaked. Products could be tampered with.
- **Transportation/Logistics**
	- Flybe, Network rail
		- If planes or trains can't move around, then people can't travel and get to work or visit family, which is bad news.

So there is a definite need to have people who can act in incident response.
***
## Definitions of Concepts:

- **Event**
	- *An event is an action occurring within a system or network.*
	- *Sending an email, mouse clicks, a firewall allowing a connection request, etc.*
- **Incident**
	- *An event with a negative consequence.*
	- *A system crash, unauthorized access to sensitive data, power failures, etc.*

Do note that there isn't a single definition of what an IT security incident is, organisations and departments define it in their own ways. In our case:

*A IT security incident is an event with clear cause to cause harm that is performed against a computer system. Examples of incidents include:*

- Data theft.
- Funds theft.
- Unauthorized access to data.
- Installation of malware and RATs (Remote Access Tools).

**Incident handling is a clearly defined set of procedures to manage and respond to security incidents in a computer or network environment.**

Incidents are not limited to intrusion alone, you have avenues such as: malicious insiders, availability issues and IP theft which fall under the umbrella of incidence response. 

A comprehensive incident response plan should address various types of incidents and provide appropriate measures to identify, contain, eradicate and recover from any security incidents ASAP so that normal function can be resumed.

Often it isn't immediately clear that `event = incident` until the problem is investigated. With this being said, there are some indicators or suspicious events that should be treated as security incidents until proven otherwise. (Suspicious communication with domains, out of the norm downloads, etc.)
***
# Incident Handling's Value and Generic Notes

IT security frequently involves the compromise of personal and business data. So we need to respond quickly to problems.

Impact can be limited to either a few devices or in other cases, large parts of our environment/network can be compromised - a great benefit to having a incident response team is that a trained force can response systematically.

This ensures that proper actions are taken and mission objectives can me prioritised. e.g. prevent/minimize the theft of data or prevent disruption of services. These objectives are achieved by **performing investigations** and **remediation steps.** The decisions that are take *before, during and after and incident will alter it's impact.*

Incidents are often rated on a scale of how critical they are by their impact on the organisation/company. The incident response team may also need to investigate issues to check if it is an IT security incident or something else.

The incident response team is often led by a **incident manager.** This role is often assigned to either a SOC (Security Operations Center) manager, CISO (Chief Information Security Officer)/CIO (Chief Information Officer) or a 3rd-party vendor (Crowdstrike Falcon Insight, Splunk Enterprise Security, etc.). Incident managers are often the single point of communication who tracks what has happened to alleviate incidents.

One of the most prolific resources used when performing incident handling is [NIST's Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf). As it aims on helping organisations mitigate the impact of any security incidents.
***
# Recap:

- Incident handling involves monitoring for events, identifying possible incidents and then remediating those incidents.
- Different organisations have different needs and will have different priorities when tackling events/incidents.
	- Companies may also have different levels of risk tolerance. e.g. JP Morgan - no/little risk, start up company medium/high risk.
- Incident handling revolves around a clear set of rules and procedures about how to react to security incidents.
- Incidents are not always just IT related.
- It is important to perform proper investigations upon events and incidents.
- We want to remediate mission critical objectives as soon as we can, then work our way down the list.
- Looking at Incident handling frameworks such as documents from NIST enables us to construct effective protocols for security incidents.








