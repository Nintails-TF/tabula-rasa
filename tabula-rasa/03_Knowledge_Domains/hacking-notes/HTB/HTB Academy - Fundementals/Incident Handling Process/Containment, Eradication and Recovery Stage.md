---
title: "Introduction:"
date modified: Friday, May 24th 2024, 11:20:51 am
---
# Introduction:

After the investigation has been completed and we have understood what type of incident and the impact of said incident has been realised, we then move on to **containment stage** to prevent the incident from causing more damage.

**Crucially, containment should happen swiftly across all systems simultaneously, otherwise we give attackers the ability to fight back and try to modify their techniques to stay inside our systems.** 
# Containment:

In the containment stage, we take action to prevent the transmission of the incident. We can divide these actions into two main categories:

1) **Short-term containment**
	1) *In this case, actions that are taken leave minimal footprint on the systems which they occur. We can achieve short-term containment via:*
		1) *Placing a system on an isolated VLAN.*
		2) *Pulling the network cable out of the system.*
		3) *Modifying an attackers C2 DNS name to a system under our control or to a fake name.*
	2) *The main purpose of short-term containment is to minimize damage and buy time for longer term remediation to take place.*
	3) *We also want to keep the systems as unaltered as possible, so we can take forensic images and preserve evidence if this hasn't been done already.*
		1) We refer this to the **backup** substage of the containment stage.
	4) *If we need to shut-down a system we have to ensure that this is communicated to the business and we have permission to do so.*
2) **Long-term containment**
	1) *Long-term containment actions - we focus on persistent actions and changes. this can often include:*
		1) *Changing user passwords.*
		2) *Applying new firewall rules*
		3) *Inserting host intrusion detection system*
		4) *Applying new system patches*
		5) *Shutting down systems.*
	2) *When we engage in these activities we need to keep the business and any relevant parties updated.*
	3) Even if a system is patched, this doesn't mean that the incident is over. We still need to start **eradication, recovery and perform post-incident activities.**
***
# Eradication:

Once an incident has been contained, eradication is required so that we can eliminate the root cause of the incident. These activities frequently include:

- Removing malware from infected systems.
- Rebuilding damaged systems.
- Restoring systems from backups.

During the eradication phase, we can extend our containment efforts by deploying new patches, hardening systems and performing network wide hardening if required.
***
# Recovery:

In the recovery stage, we bring our systems back to normal operation. However; the business needs to check that the systems are working as expected and that we aren't missing any data.

Once everything has been verified, systems are brought back to production and business and services continue as usual. All these restored systems should be subject to heavy logging and monitoring for the next while, as these compromised systems tends to be targets again if the adversary regains access to the environment in a short period of time.

Typical suspicious events are:
- Unusual logins
	- e.g. user or service accounts that have never been logged into are inactive.
- Unusual processes
- Changes to registry in locations that are usually modified by malware.

Recovery stage in some large incidents may take months, these are usually broken into phases:

- Early phases focus on increasing the overall security level to prevent further incidents through quick wins and the elimination of low hanging fruit.
- Later phases focus on permanent long-term changes to keep the organisation as secure as possible.
***
# Recap:

- We use both short-term and long-term containment methods to neutralise the effect of security incidents.
	- Short-term containment seeks to mitigate immediate damage
	- Long term containment seeks to raise the security of our system with persistent acts and changes.
- It is important to realise after we have contained the incident we then need to move on to eradication, then recovery, then post-incident reporting and meetings.
- Eradication involves eliminating the root causes of the incident.
	- We do this by removing malware, rebuilding damaged systems and restoring from backups.
- Recovery involves bringing systems back online and monitoring them to see if they are missing any data.
	- We want to make sure that we harden and monitor the holes that we have plugged, as attackers are likely to try the same exploit again.
	- Remove low-hanging fruit and easy exploits.
