---
date created: Wednesday, October 15th 2025, 3:10:51 pm
date modified: Thursday, October 16th 2025, 11:53:19 am
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#Enrichment|Enrichment]]"
---

# What is Enrichment?

Enrichment is the process of adding context to parsed logs to make them more meaningful for analysis. In essence: raw logs tell you what happened whilst enriched logs/data tells you why it matters.
## Types of Enrichment:

### Threat Intelligence Enrichment:

By comparing log data against known bad indicators or actors, log data can be enhanced to track and monitor threats.

```JSON
Original Log:
{
  "source_ip": "45.142.212.61",
  "destination_ip": "192.168.1.50",
  "action": "blocked"
}

After Threat Intel Enrichment:
{
  "source_ip": "45.142.212.61",
  "destination_ip": "192.168.1.50",
  "action": "blocked",
  "threat_intel": {
    "reputation": "malicious",
    "category": "C2_server",
    "first_seen": "2025-09-12",
    "threat_actors": ["APT28"],
    "confidence": "high"
  }
}
```

**Sources:**
- Alien Vault OTX
- Abuse.ch
- MISP (Malware Information Sharing Platform)
- Commercial Feeds (Recorded Future, ThreatConnect, etc)

### Geolocation Enrichment:

By adding geographic context to IP addresses, you can detect user logs or data from differing locations and track impossible travel (US login, then to China 10 minutes later).

```JSON
Original:
{
  "destination_ip": "192.168.1.100"
}

Enriched:
{
  "destination_ip": "192.168.1.100",
  "asset": {
    "hostname": "DC01.corp.local",
    "role": "domain_controller",
    "os": "Windows Server 2019",
    "criticality": "HIGH",
    "owner": "IT Department",
    "patch_level": "current"
  }
}
```

You can see where an attack is heading, if something is an attack on a test server, then the priority is low. If it is an attack on a domain controller, then it is critical.

### User/Identity Enrichment

By adding HR or active directory data, we can see if a user or actor is access regular resources or is accessing suspicious resources.

```JSON
Original:
{
  "username": "jsmith"
}

Enriched:
{
  "username": "jsmith",
  "user_info": {
    "full_name": "John Smith",
    "department": "Finance",
    "title": "Senior Accountant",
    "manager": "Jane Doe",
    "privileged_account": false,
    "last_password_change": "2025-09-20"
  }
}
```

If a finance user is accessing financial details, that's normal. Where as if said user is accessing firewall configs, that's suspicious. Similarly if an admin account is working outside of regular hours, we can raise an alert.

## Practical Application of Enrichment:

So why is enrichment valuable? The main reasons are:

1. To add context to raw logs.
	1. *Raw logs are often cryptic, enrichment gives more understanding of what is really happening.*
2. To improve true positive rates and reduce false positives.
	1. *Failed login from corporate VPNs can be ignored, whilst failed login from TOR exit nodes flagged as high-risk IP triggers an alert.*
3. To speed up investigations
	1. *When all the data can be seen up front, analysts don't have to manually look through data in multiple tools.*
	2. *This leads to faster triage, reduced MTTD and MTTR.*
		1. *Mean time to Detect.*
		2. *Mean Time to Respond.*
4. To integrate external threat intelligence
	1. *By pulling data from external feeds, enrichment can automatically add data from these sources to detect known threats quicker.*
5. To support correlation and automation.
	1. *Enriched data from SIEM and SOAR systems correlate events across users, devices, and systems.*
	2. *This allows systems to automatically link related events.*
		1. *Multiple failed login attempts -> privilege escalation -> file exfiltration, etc.*
6. Provide business relevance to assist risk management.
	1. *Alerts can be prioritised and explained clearly and urgent data can be secured.*

## Enrichment Challenges
- **Performance overhead** (looking up every IP against threat intel databases)
- **Stale data** (threat intel updates daily, but logs are real-time)
- **False positives** (legitimate IPs on threat lists)
- **Cost** (commercial threat intel feeds are expensive)