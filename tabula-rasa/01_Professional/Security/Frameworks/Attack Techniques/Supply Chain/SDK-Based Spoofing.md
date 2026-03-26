---
date created: Sunday, March 8th 2026, 1:47:59 pm
date modified: Sunday, March 8th 2026, 2:02:44 pm
---

# SDK-Based Residential Proxy Farming


## SDK-Based Residential Proxy Enrollment — MITRE ATT&CK Mapping

Before mapping it out, it's worth noting that SDK-based methods are unusual in the ATT&CK framework because they blur the line between **social engineering, supply chain attack, and technical compromise** — sometimes all three simultaneously. The "attack" in many cases doesn't look like an attack at all, which is precisely what makes it effective.

---

## Tactic 1: Reconnaissance

_Goal: Identify target platforms and user populations worth compromising at scale_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Gather Victim Identity Information|T1589|Identifying high-volume app categories where users expect free services — VPNs, games, utilities — and are therefore primed to accept broad permissions|
|Search Open Technical Databases|T1596|Researching app store metrics, download volumes, and user demographics to identify the highest-yield platforms for SDK embedding|
|Gather Victim Org Information: Software|T1592.002|Identifying which app developers are financially struggling or actively seeking monetization partners — the most likely to accept SDK deals without scrutiny|

This phase is often conducted as straightforward market research rather than anything recognizable as attack behaviour.

---

## Tactic 2: Resource Development

_Goal: Build the infrastructure and tools needed to execute and monetize the operation_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Develop Capabilities: Malware|T1587.001|Developing the SDK itself — the proxy enrollment code that will be embedded in third-party apps|
|Acquire Infrastructure: Server|T1583.004|Building the C2 and proxy management infrastructure that enrolled devices will phone home to|
|Establish Accounts|T1585|Creating legitimate-appearing developer accounts, company registrations, and SDK marketplace listings to present the operation as a credible business|
|Obtain Capabilities|T1588|Acquiring or licensing existing proxy management frameworks rather than building from scratch|
|Develop Capabilities: Digital Certificates|T1587.003|Obtaining legitimate SSL certificates for C2 infrastructure to make traffic look indistinguishable from normal HTTPS|

This tactic is where the **business legitimization** of the operation happens. Companies like the one behind 911 S5 registered actual businesses, had websites, and presented themselves as legitimate SDK providers to app developers.

---

## Tactic 3: Initial Access

_Goal: Get the SDK onto victim devices at scale_

This is the most complex tactic in the SDK model because there are multiple distinct pathways, each with its own ATT&CK mapping.

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Supply Chain Compromise: Software Supply Chain|T1195.002|Embedding the SDK into third-party apps that are then distributed through legitimate app stores — the app developer becomes an unwitting (or witting) vector|
|Phishing: Spearphishing Link|T1566.002|Targeting app developers directly with offers to monetize their apps through the SDK, essentially social engineering the developer rather than the end user|
|Drive-by Compromise|T1189|Malicious websites or ad networks that prompt SDK-containing app downloads outside official stores|
|Valid Accounts|T1078|In cases where the SDK operator bribes or compromises an app developer's store account to push SDK updates to existing installs|
|Replication Through Removable Media|T1091|Less common but documented — SDK-containing apps distributed via sideloading through unofficial channels|

The **supply chain compromise pathway** deserves particular attention here. When an SDK is embedded in a legitimate app by the app developer — whether knowingly or unknowingly — every subsequent install of that app is a successful initial access event that required no direct interaction with the victim whatsoever. The victim downloads what appears to be a normal app from a trusted store.

---

## Tactic 4: Execution

_Goal: Run the proxy enrolment code on the victim device_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|User Execution: Malicious File|T1204.002|The user installing the app is the execution event — no exploit required|
|Shared Modules|T1129|SDK code loading as a shared library within the host app's process space|
|Scheduled Task/Job|T1053|SDK configuring background tasks or scheduled jobs to ensure proxy functionality persists even when the app isn't actively in use|
|Native API|T1106|SDK using platform APIs (Android's WorkManager, iOS Background App Refresh) to maintain background network activity within OS-permitted boundaries|

The critical insight here is that **execution requires no privilege escalation and no exploit**. The SDK runs within the permissions the user already granted to the app — network access, run in background — which are standard permissions that most users accept without consideration.

---

## Tactic 5: Persistence

_Goal: Ensure the device remains enrolled in the proxy network across reboots, app updates, and user inactivity_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Boot or Logon Autostart Execution|T1547|Registering the SDK as a service that starts automatically when the device boots|
|Event Triggered Execution|T1546|Configuring the SDK to activate on network connectivity events — device connects to WiFi, SDK wakes and begins routing traffic|
|Scheduled Task/Job: Cron|T1053.003|Periodic check-ins with C2 infrastructure to receive updated configuration and confirm continued enrollment|
|Modify Existing Service|T1031|Integrating proxy functionality into existing system services to reduce visibility|

On Android in particular, persistence is relatively straightforward because the OS has historically allowed background services to run with minimal restriction. iOS is harder — Apple's stricter background execution limits mean SDK operators on iOS rely more heavily on opportunistic execution during active app use.

---

## Tactic 6: Defence Evasion

_Goal: Avoid detection by the user, the platform, app store reviewers, and security tools_

This is arguably where the SDK model is most sophisticated, and where it differs most sharply from wardriving or traditional malware.

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Masquerading|T1036|The SDK presents itself as a legitimate monetization or analytics library — indistinguishable from the dozens of other SDKs in any modern app|
|Obfuscated Files or Information|T1027|SDK code is obfuscated to resist reverse engineering by app store reviewers or security researchers|
|Signed Binary Proxy Execution|T1218|Proxy traffic executes within a legitimately signed, store-approved app — inheriting its trust|
|Traffic Signaling|T1205|C2 communications hidden within normal-looking HTTPS traffic, using legitimate-appearing domains and certificates|
|Indicator Removal|T1070|Minimizing local logging of proxy activity on the device|
|Subvert Trust Controls|T1553|Leveraging the host app's existing user trust and store approval to avoid scrutiny|
|Hide Artifacts|T1564|SDK functionality deliberately separated from the visible app functionality to resist casual inspection|

The **app store review bypass** deserves specific mention. Both Google Play and the Apple App Store have automated and manual review processes. SDK operators have developed specific techniques to evade these:

- **Delayed activation** — the SDK behaves normally during the review period (detectable by running on known review IP ranges or sandboxed environments) and activates only after a certain time post-install or after detecting it's running on a real user device
- **Remote configuration** — the SDK ships in an inert state and receives its proxy configuration from a C2 server after installation, meaning the malicious functionality isn't present during review
- **Legitimate SDK mimicry** — the code structure deliberately mirrors well-known legitimate SDKs like analytics or advertising libraries

---

## Tactic 7: Command and Control

_Goal: Manage enrolled devices and broker their bandwidth to paying customers_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Application Layer Protocol: Web Protocols|T1071.001|C2 communication over standard HTTPS — indistinguishable from normal app traffic|
|Proxy: External Proxy|T1090.002|Enrolled devices acting as proxy nodes for customer traffic|
|Proxy: Multi-hop Proxy|T1090.003|Chaining multiple enrolled devices to further obscure traffic origin|
|Dynamic Resolution|T1568|Using domain generation algorithms or fast-flux DNS to make C2 infrastructure harder to block|
|Ingress Tool Transfer|T1105|Pushing updated proxy configurations or SDK components to enrolled devices|
|Non-Application Layer Protocol|T1095|Some implementations use UDP-based protocols for lower-overhead proxy traffic|

The C2 infrastructure in a mature SDK-based operation is essentially indistinguishable from a legitimate cloud service backend. Traffic from an enrolled device to the operator's servers looks identical to any other app phoning home to its backend — which is intentional.

---

## Tactic 8: Collection

_Goal: Opportunistic data collection from enrolled devices and their traffic_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Data from Local System|T1005|Some SDK implementations collect device identifiers, installed app lists, and network configuration beyond what's needed for proxy functionality|
|Network Sniffing|T1040|Traffic routed through the device may be inspected before forwarding|
|Adversary-in-the-Middle|T1557|In more aggressive implementations, the SDK can intercept and inspect traffic from other apps on the same device|
|Data from Information Repositories|T1213|Collecting browsing history, DNS query logs, and connection metadata from the device|

Not all SDK proxy operations engage in collection beyond what's needed to operate the proxy. But the capability exists and the temptation to monetize that additional data is significant given the same infrastructure supports it.

---

## Tactic 9: Exfiltration

_Goal: Move collected data out of the device to operator infrastructure_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Exfiltration Over C2 Channel|T1041|Device telemetry and collected data piggybacked on the same C2 communications used to manage proxy enrollment|
|Scheduled Transfer|T1029|Batching data collection and transmitting during off-peak hours to minimize detectability|
|Exfiltration Over Alternative Protocol|T1048|Using DNS queries or other low-profile protocols to exfiltrate small amounts of data|

---

## Tactic 10: Impact

_Goal: The downstream effects of the deployed proxy network_

|Technique|ATT&CK ID|How SDK Methods Apply|
|---|---|---|
|Resource Hijacking|T1496|Using victim bandwidth and IP addresses as a commercial product without compensation|
|Network Denial of Service|T1498|Proxy pool being sold to customers conducting DDoS attacks — the enrolled device participates without the owner's knowledge|
|Endpoint Denial of Service|T1499|Credential stuffing and account takeover attacks conducted through the proxy pool|
|Financial Theft|T1657|Ad fraud, payment fraud, and other financially motivated crimes conducted through enrolled devices' IPs|

---

## How It Compares to Wardriving in the Framework

Mapping both side by side reveals some important structural differences:

**Wardriving** is geographically constrained, labour intensive per node, produces high-quality sticky IPs, requires physical presence, and the attack surface is the router — a device the victim rarely monitors or understands.

**SDK enrolment** is geographically unlimited, infinitely scalable, requires no physical presence, produces IPs that move with the device, and the attack surface is human psychology and app store trust — exploiting the fact that users install apps without scrutiny and grant permissions without understanding them.

The ATT&CK mapping reflects this — wardriving maps heavily to **Initial Access and Persistence** tactics focused on technical exploitation, while SDK methods map more heavily to **Resource Development and Defence Evasion** tactics focused on legitimacy manufacturing and trust exploitation.

Both ultimately feed the same supply chain. But the SDK model's ability to scale to millions of nodes globally without any physical constraint is why it has become the dominant acquisition method in the residential proxy market, with wardriving occupying a complementary niche for higher-quality, geographically targeted IP acquisition.