---
date created: Wednesday, October 15th 2025, 3:11:11 pm
date modified: Thursday, October 16th 2025, 12:30:45 pm
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#Retention Policies|Retention Policy ]]"
---

# Retention Polices

## Retention Tiers (Hot / Warm / Cold / Frozen)

| **Tier**   | **Duration**   | **Description**             | **Performance / Storage**                    | **Use Case**            | **Cost** |
| ---------- | -------------- | --------------------------- | -------------------------------------------- | ----------------------- | -------- |
| **HOT**    | 0–7 days       | Actively written to         | Fastest (SSD)                                | Real-time alerting      | 💰💰💰💰 |
| **WARM**   | 7–90 days      | Immutable, still searchable | Slightly slower, compressed (50–70% savings) | Ongoing investigations  | 💰💰💰   |
| **COLD**   | 90 days–1 year | Heavily compressed          | Slower searches (S3 / slower disks)          | Historical analysis     | 💰💰     |
| **FROZEN** | 1+ years       | Archived, not searchable    | Offline or glacier/tape                      | Compliance / Legal hold | 💰       |
### Example Cost Breakdown

|**Tier**|**Duration**|**Storage**|**Cost/GB/month**|**Total Cost**|
|---|---|---|---|---|
|Hot (SSD)|7 days|700 GB|$0.10|**$70/month**|
|Warm (HDD)|30 days|3 TB|$0.03|**$90/month**|
|Cold (S3)|90 days|9 TB|$0.01|**$90/month**|
|Frozen (Glacier)|1 year|36.5 TB|$0.004|**$146/month**|
|**Total (Tiered)**|—|**49.2 TB**|—|**$396/month**|
|**Without Tiering (All SSD)**|—|49.2 TB|$0.10|**$4,920/month (12× more expensive)**|

> [!tip]  
> **Rule of thumb:** the _older_ the data, the _cheaper_ the storage — but also the _slower_ the access.

---

## Compliance-Driven Retention

|**Regulation**|**Retention Requirement**|**Scope**|
|---|---|---|
|**PCI DSS**|1 year online, 3 months immediately accessible|Cardholder data access logs|
|**HIPAA**|6 years|PHI access logs|
|**GDPR**|“As long as necessary” + right to deletion|Personal data processing logs|
|**SOX**|7 years|Financial system logs|
|**GLBA**|3–6 years|Banking / financial logs|

> [!important]  
> Always align your SIEM retention with **legal and regulatory requirements**, not just storage limits.

---

## Typical Retention Strategy

### Small Organization (≈10 GB/day)

```text
- 30 days hot  →  300 GB (SSD)
- 60 days warm →  600 GB (HDD)
- 1 year cold  →  3.6 TB (S3/Object Storage)
- 7 years frozen → Glacier/Tape
```

### Large Organization (≈1 TB/day)

```text
- 7 days hot   →  7 TB (SSD)
- 30 days warm → 30 TB (HDD)
- 90 days cold → 90 TB (S3 Standard)
- 1 year frozen → 365 TB (S3 Glacier)
- 7 years archived → Tape/Offline
```

---

## Retention Best Practices

- **Separate by criticality:**
    - Domain controller logs → 1 year hot
    - Printer logs → 30 days hot → delete
- **By log type:**
    - Security logs → long retention
    - Application/debug logs → short retention
- **Legal hold:**
    - Freeze deletion if litigation is pending
- **Test restoration:**
    - Ensure archived data can actually be recovered when needed

---
## Configuring Retention

|**SIEM**|**Retention Configuration**|
|---|---|
|**Splunk**|Define retention in `indexes.conf` (`frozenTimePeriodInSecs` or `maxTotalDataSizeMB`)|
|**Elastic Stack**|Use Index Lifecycle Management (ILM) policies for hot/warm/cold/frozen tiers|
|**QRadar**|Configure retention buckets via “Ariel Database Management”|
|**Microsoft Sentinel**|Adjust “Log Analytics Workspace” data retention (default 30–730 days)|
