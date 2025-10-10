---
title: "Introduction:"
date modified: Sunday, May 26th 2024, 3:41:39 pm
---
# Introduction:

At this point we have now created processes and procedures on how to handle security incidents.

This brings us to the next stage **detection and analysis** this involves all aspects of detecting an incident such as:

- Information from sensors, logs and trained personnel.
- Information and knowledge sharing.
- Context based threat intelligence

Other important factors include: having a clear understanding of the architecture, segmentation of the architecture and visibility within the network.

**Threats** are introduced to an organisation in infinite amount of different attack vectors. For example:

1. *An employee notices abnormal behavior.*
2. *An alert from one of our tools*
	1. *EDR, IDS, Firewall, SIEM, etc.*
3. Threat hunting activities.
4. Third-party notifications informing us of a compromise.

We want to understand what levels these attacks are at, by referencing the place they are in our network at:

1. Detection at the perimeter of our network.
	1. *Via firewalls, internet-facing networks intrusion/detection/prevention systems, DMZ, etc.*
2. Detection at the internal network level.
	1. *Via local firewalls, host intrusion detection/prevention systems, etc.*
3. Detection at the endpoint level.
	1. *Via AV, endpoint detection and response systems, etc.*
4. Detection at the application level.
	1. *Via application logs, services logs, etc.*
***
# Initial Investigation:

If a security incident is detected, first things first, we want to start gathering some initial information and establish context before assembling a team of people and having an organisational-wide response.

*If we don't have a concrete timeline, we can jump to incorrect or misled conclusions which will slow down the investigation.* For example, an admin account connects to an IP address at HH:MM:SS, but we don't know what IP address and timezone refers to.

To sum up, we should collect as much information about a few following factors:
1. Date/time of when the incident was reported. Also, who detected the incident/reported the incident.
2. How was the incident detected?
3. What was the incident? Phishing? System unavailability? etc.
4. Assemble a list of impacted systems
5. Document who has accessed the impacted systems and what actions have been taken.
	1. Make a note of the incident is ongoing or suspicious activity has stopped.
6. Physical location, operating system, IP addresses and host names, system owner, system's purpose and current state of the machine.
7. **If malware is involved,** List of IP addresses, time and date of detection, type of malware, systems impacted, export of malicious files with forensic information on them.
	1. Forensic info includes hashes, copies of files, etc.

Once we have this initial information, we can make decisions based on the knowledge that we have gathered. Generally this means that the more widespread the incident is or if it effect high profile individuals (CEOs, C-suite members, etc.) the more seriously we should treat it.

The main thing we want to do is to construct a **timeline of events.** 

This timeline can expose on if newly discovered evidence is part of the current incident. e.g. what we thought was the initial payload of the attack, has been found on another device two weeks ago. 

Sometimes we will uncover extremely useful data, other times we will look in the wrong place and uncover unrelated data. But we should keep our timeline updated with key info. Our timeline should be constructed like so:

|`Date`|`Time of the event`|`hostname`|`event description`|`data source`|
|---|---|---|---|---|
|09/09/2021|13:31 CET|SQLServer01|Hacker tool 'Mimikatz' was detected|Antivirus Software|
Describing attacker behavior is very important, so activities that highlight:
1) When an attack occurred
2) When a network connection was established to access a system.
3) When files were downloaded.
Are critical.

Finally, we also want to diagnose where the activity was detected/discovered from and the systems that are associate with it.
***
# Incident Severity and Extent Questions:

When handling a security incident, we should also try to answer the following questions:
- What is the exploits impact?
- What are the exploits requirements?
- Can any business-critical systems be affected by the incident?
- Are there any suggested remediation steps?
- How many systems have been impacted?
- Has the exploit been used in the wild before?
- Does the exploit have any worm-like capabilities?

The final two can indicate the level of sophistication by an adversary - if the exploit isn't used in the wild and the exploit is worm-like we can assume that the adversary is relatively advanced.

The exploits with the highest level of impacts will be handled promptly and incidents with high numbers of impacted systems will also have to be escalated.
***
# Incident Confidentiality and Communication:

Incidents are very confidential topics, so information should be rationed out on a need-to-know basis - unless various laws or management decisions instruct us otherwise. 

This is because the adversary can be an employee or if a breach has occurred, communication should be deferred to internal/external parties that manage the legal department.

When an investigation is launched, we have various expectations and goals. Often we what to figure out:

- The type of incident that occurred
- The sources of evidence we have available. 
- A rough estimation on how much time the team needs to investigate the incident.
- If we can unmask the adversary or not.

These may change as the investigation develops, our goals may change and adapt, you should also take care to info management and others about these modified expectations.
***
# Analysing Investigations:

Once we start an investigation we want to **understand what and how it happened.** To analyse the incident-related data properly and efficiently - our team members need deep technical knowledge and experience in the field.

One may end up asking:
1. *Why do we care about why the incident happened?*
2. *Why don't we simply rebuild the impacted system and basically forget that an incident ever happened?*

Mainly, we need to understand the attack, so that it cannot be replicated in the future. So we want to understand how the adversary got in, what tools they used, and which systems were impacted.
***
# The Investigation:

Investigation starts based on the initially gathered (limited) data that we know about the incident so far. With this initial data, we start a 3-step process that will iterate and loop as the investigation involves, this includes:

1) Creation and usage of indicators of compromise. (IOC)
2) Identification of the new leads and impacted systems.
3) Data collection and analysis form the new leads and impacted systems.

We can express this in a flowchart:
![[Pasted image 20240523204003.png]]
## Initial Investigation Data:

In order to reach a conclusion, an investigation should be based on valid leads that have been discovered during this initial phase but throughout the whole investigation process. The incident handling team should bring up new leads constantly and not tunnel on finding a specific lead.

Narrowing an investigation down to a specific activity results in limited findings, premature conclusions and an incomplete understanding of the incident's impact.
## Creation and Usage of IOCs:

An **Indicator Of Compromise (IOC)** is a sign that an incident has occurred. IOCs are documented in a structured manner which represents that artifacts that have been compromised.

Examples of IOCs can be:
- IP addresses
- Hash values of files
- files names

IOCs are often so important to an investigation that we have special languages like [**OpenIOC**](https://github.com/fireeye/OpenIOC_1.1)have been developed to document and share them in a standardized manner. Another useful tool is **[Yara](https://library.mosse-institute.com/articles/2022/05/yara-a-powerful-malware-analysis-tool-for-detecting-ioc-s-part-1/yara-a-powerful-malware-analysis-tool-for-detecting-ioc-s-part-1.html)** for creating IOCs. Another tool is [Mandiant's IOC editor](https://fireeye.market/apps/S7cWpi9W)

Using these tools we can use the artifacts that we uncover to create, edit and share IOCs. We can even import IOCs from third parties if the adversary or attack is known.

To leverage the strength of IOCs, we need to deploy IOC-obtaining or searching tools at scale. Such tools are:

- WMI or powershell.
	- *Do note we have to be careful to prevent the creds of highly privileged users from being cached when connecting to compromised systems. *
	- WinRM is an example of a Network login that doesn't cache credentials. But any logon type 3 typically don't cache any creds.
- PsExec
	- When PsExec is used with explicit credentials, these credentials are cached on the local system. When PsExec is used without credentials throughout the session of the currently logged on user, the creds aren't cached.
	- The same tool leaves different traces depending on the state.
***
# Identification of New Leads and Impacted Systems:

After searching for IOCs, you expect some hits to reveal other systems wit the same signs of compromise. We may hit false positives with overly generic IOCs. We need to eliminate these cases.

We can also end up in a position where we come across a large number of hits. In this case, we should prioritize the leads that can provide us with new leads after a forensic analysis.
***
# Data Collection and Analysis from new leads and Impacted Systems:

Once we have identified systems that included our IOCs, we want to collect and preserve the state of those systems for further analysis in order to uncover new leads and/or answer investigative questions about the incident.

Depending on the system, there are multiple approaches on how to collect data, sometimes we want to perform a *live response* on a system as it is running, on other cases we want to shut down systems then analyse it.

**Live response** is the most common approach where we are able to collect a predefined set of data that is rich in artifacts that can explain what has happened to a system. 

Shutting down a system is not an easy call to make, because artifacts may only be available in RAM - which we will lose if the system is powered off. 

No matter what method we choose, it is vital we minimise the interaction with the system to avoid altering any artifacts. Once data has been collected, we need to analyse it, this is often the most time-consuming process during an incident.

**Malware analysis** and **disk forensics** are the most common examination types. Any newly discovered data and leads are added to the time line, which is constantly updated. **Memory forensics** is also a capability which is becoming more popular and is very relevant when dealing with advanced attacks.

During the data collection process, we need to keep track of the **chain of custody** to ensure that the examined data is court-admissible if legal action can be taken against an adversary.
***
# Recap:

- The detection phase revolves around the following
	- Using various tools/resources to gather information about the adversary.
		- Logs, trained staff, sensors, etc.
	- These threats can be detected at various places in the network.
		- At the perimeter, internal network, endpoint level or at the application layer.
- If we detect an incident, the most important thing we want to do is it gather critical information and construct a time line.
- Depending on the severity of the incident/threat will influence if it is escalated to management or C-suite executives.
- When evaluating incident severity, we want to note how widespread the issue is and how difficulty is it to fix, along with the level of sophistication by the adversary.
- We want to be confidential with security incidents and set realistic goals and expectations.

- The analysis phase revolves around the following
	- Why did this incident happen and how did it happen?
- The investigation should gather initial data, then follow the three step iterative process:
	1) Create IOCs
	2) Identify new leads
	3) Collect more data then generate more leads/IOCs
- We must be careful not to narrow the scope of the investigation too early.
- IOCs can be shared using various tools and enable us to quickly document case artifacts.
	- Though we can hit false positives.
- We generally want to perform **live response** so we can capture as much info as possible.
	- We may want to shut down systems, but we will lose data in RAM.
		- We should get permission before doing this and store the RAM data forensically for analysis.
	- 



