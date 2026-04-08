---
date created: Sunday, March 8th 2026, 1:31:37 pm
date modified: Sunday, March 8th 2026, 1:34:12 pm
---

# Wardriving and Walking:

### Tactic 1: Reconnaissance

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Active Scanning: Wireless Network Scanning|T1595.002|Beacon frame capture via monitor mode, SSID and encryption profiling|
|Gather Victim Network Information|T1590|MAC OUI identification, signal mapping, WPS detection|
|Gather Victim Host Information|T1592|Identifying connected devices, router models, firmware versions|
### Tactic 2: Resource Development

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Acquire Infrastructure: Compromised Network Devices|T1584.008|Compromised routers become proxy nodes or attack relay points|
|Compromise Accounts|T1586|Capturing credentials from compromised network traffic|
### Tactic 3: Initial Access

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Exploit Public-Facing Application|T1190|Exploiting WPS vulnerability, attacking router admin panel|
|Valid Accounts: Default Accounts|T1078.001|Using manufacturer default credentials against the router admin interface|
|Drive-by Compromise|T1189|Serving malicious content to devices on the compromised network|
|External Remote Services|T1133|Accessing router management interfaces exposed to the network|

### Tactic 4: Persistence

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Pre-OS Boot: System Firmware|T1542.001|Flashing malicious firmware onto the compromised router|
|Modify System Image|T1601|Altering router firmware to create a persistent backdoor|
|Account Manipulation|T1098|Adding attacker-controlled admin accounts to the router|
|Traffic Signaling|T1205|Configuring the router to respond to covert signals from a C2 server|

This is the **warkitting** variant, where the goal isn't just access but permanent, stealthy control.
You could also just sell these proxies as residential.

### Tactic 5: Defence Evasion

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Proxy: Multi-hop Proxy|T1090.003|Routing attack traffic through chains of compromised residential routers|
|Masquerading|T1036|Attack traffic appearing to originate from legitimate residential IPs|
|Rootkit|T1014|Hiding malicious processes within compromised router firmware|
|Impair Defenses|T1562|Disabling router logging, firewall rules, or automatic update mechanisms|
### Tactic 6: Collection

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Adversary-in-the-Middle|T1557|Intercepting traffic between network devices and the internet|
|Network Sniffing|T1040|Capturing unencrypted credentials, session tokens, DNS queries|
|Man-in-the-Browser|T1185|SSL stripping attacks against connected devices' browser sessions|
### Tactic 7: Command and Control

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Proxy: External Proxy|T1090.002|Compromised routers relay C2 traffic for other malware campaigns|
|Protocol Tunneling|T1572|Encapsulating C2 communications within normal-looking DNS or HTTP traffic through the router|
|Non-Standard Port|T1571|Using unexpected ports on the router for covert C2 channels|
### Tactic 8: Impact

|Technique|ATT&CK ID|How Wardriving Applies|
|---|---|---|
|Network Denial of Service|T1498|Using compromised router pools to launch DDoS attacks|
|Endpoint Denial of Service|T1499|Targeting specific services through the anonymizing proxy layer|
|Resource Hijacking|T1496|Using compromised routers for cryptomining or proxy bandwidth resale|

---
