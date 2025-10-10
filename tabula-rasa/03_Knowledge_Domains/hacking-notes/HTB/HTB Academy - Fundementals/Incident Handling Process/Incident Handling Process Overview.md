---
title: "Introduction:"
date modified: Sunday, May 26th 2024, 3:44:56 pm
---
# Introduction:

Just like the cyber kill chain, we have different stages of the **incident handling process.** This process gives organisations a methodology to follow for preparing, detecting and responding to malicious events.

NIST defines the **incident handling process** as the following:
![[Pasted image 20240520171810.png]]

When working as an **incident handler** we usually spend most of our time in the first two stages - **preparation and detection & analysis.** This is when we spent a lot of time improving ourselves and looking for the next malicious event. After we detect a event, we then can move onto the next stage and respond to the event.

**There must always be resources operating on the first two steps, this is because it ensures that a system can remain operational and secure.** 

*If preparation stops, then we can get blindsided by a new form of attack or exploit.*
*If detection stops, then we can be unaware of threats that may be lurking within.*

For example, If we discover 10 infected machines, we shouldn't contain 5 of them - eradicate them, then do the same again. This can indicate to the attackers that you have discovered them and they can take counter-measures. *We would want to contain all 10 systems first, then move to the eradication process.*
***
# Investigation and Recovery:

During incident handling the two main activities are: **investigating and recovering:**

The main goal of **investigation** is to answer the following questions:
1. Discover the *patient zero* system and create (or update) and incident timeline.
2. Determine what tools and malware the adversary used.
3. Document the compromised system and what the adversary has done.

The main goal of **recovery** is to answer the following questions:
1. Creating a recovery plan (Or using/adapting a previous plan).
2. Implementing recovery actions

Once all the fires have been put out and incidents resolved, a **lessons learned** activity is performed, which seeks to document the good and the bad of what happened, to indicate what should happen if a similar event happens again.

***
# Recap 

- NIST defines an incident handling process which includes:
	1) Preparation.
	2) Detection and Analysis.
	3) Containment, Eradication and Recovery.
	4) Post-Incident activity.
- We mainly spend our time **preparing and detecting/analysing** threats.
	- We need to ensure that our team is always preparing and detecting threats.
- The purpose of investigations is to figure out what has happened and recovery seeks to find out how to fix our systems.
- Always have a lessons learned section or a recap on what went wrong/right, so that changes can be made for the future.
