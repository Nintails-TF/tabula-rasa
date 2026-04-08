---
date created: Wednesday, October 15th 2025, 3:11:11 pm
date modified: Thursday, October 16th 2025, 12:43:10 pm
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#Query Languages|Query Languages]]"
---

# What Are Query Languages?

Query languages are how analysts interface with SIEMs to search, filter, and analyse data. Different SIEMs use different query languages.

### Splunk - SPL (Search Processing Language)

SPL is most similar to Unix pipes in there structure, for example:
```spl
index=security sourcetype=WinEventLog:Security EventCode=4624
| stats count by user
| sort -count
```

**Where:**
1. `index=security` → Which data store (Security)
2. `sourcetype=WinEventLog:Security` → What type of logs
3. `EventCode=4624` → Successful logons
4. `| stats count by user` → Count events per user
5. `| sort -count` → Show highest first

#### SPL Strengths:
- Intuitive pipeline syntax
- Powerful for statistics and dashboards
- Excellent documentation
#### SPL Weaknesses:
- Proprietary (only works in Splunk)
- Can be slow on large datasets (no SQL-style optimization)

***

### Elastic/Microsoft - KQL (Kusto Query Language):

KQL is similar to SQL but is optimized for time-series data, for example:
```kql
SecurityEvent 
| where EventID == 4624 
| summarize count() by Account 
| sort by count_ desc
```

**Where:**
- `SecurityEvent` → Table/index name
- `| where EventID == 4624` → Filter condition
- `| summarize count() by Account` → Aggregate
- `| sort by count_ desc` → Order results

**KQL Strengths:** 
- Fast on Azure/Elastic infrastructure 
- SQL-like (familiar to many analysts) 
- Great for time-series analysis 

**KQL Weaknesses:** 
- Less mature than SPL 
- Microsoft-centric (though used in Elastic)

### Lucene Searching in Elastic:

Lucene searching uses simple queries and is used for quick searches and ad-hoc investigation.

``` lucene
source_ip:10.0.0.5 AND event_id:4625 
```

***

### Query Optimization Tips

**DO:**
- ✅ Use indexed fields when possible
- ✅ Filter early (reduce dataset size first)
- ✅ Use time bounds (last 24h, not "all time")
- ✅ Test on small time ranges first

**DON'T:**
- ❌ Use wildcards at the start of strings (`*admin`)
- ❌ Search all indexes unless necessary
- ❌ Use complex regex on millions of events
- ❌ Extract fields unnecessarily

**Example - Bad vs Good:**

✅ Good (fast):
```spl
index=security sourcetype=WinEventLog:Security user=*admin* earliest=-24h | stats count
```

❌ Bad (slow):

```spl
index=* sourcetype=* 
| regex user=".*admin.*" 
| stats count
```