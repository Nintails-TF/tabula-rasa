---
date created: Wednesday, October 15th 2025, 3:11:11 pm
date modified: Thursday, October 16th 2025, 12:24:49 pm
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#Indexing|Indexing]]"
---

# What is Indexing?

Indexing is the process of organizing parsed and enriched data so that it can be searched and queried quickly, even across billions of events.

It is similar to the Dewey decimal system in libraries, without indexing it's a pain to find a book you want, with indexing you speed up that process.

## How Does Indexing Work in SIEMs?

### Traditional Database Approach:

The traditional approach is much simpler to develop, but it's not an efficient query, meaning searching is slow - fine enough for small sets of data, but poor for scaling:
```SQL
SELECT * FROM logs WHERE source_ip = '10.0.0.5'; -- Scans every row in the table (millions/billions of rows) -- Takes minutes to hours
```

### SIEM Indexing Approach

We can search for matches in data rather than all data, we want to minimize the amount of data that we index and only collect what matters:
```SQL
Build an inverted index (like a book index):

"10.0.0.5" → [Event 1, Event 54, Event 203, Event 4991, ...] 
"admin" → [Event 2, Event 54, Event 199, Event 5002, ...] 
"4624" → [Event 54, Event 199, Event 201, Event 4991, ...]

Search for source_ip="10.0.0.5" AND user="admin": 
→ Look up "10.0.0.5" → [1, 54, 203, 4991] 
→ Look up "admin" → [2, 54, 199, 5002] 
→ Intersection → [54] ← Only event that matches both 

Result in milliseconds, even with 100GB of logs.
```

### Indexing Structure:

Most SIEMs partition data by time - since security investigations are time-sensitive:
```SQL
Index Structure: 
├── logs-2025-10-15-00 (12am-1am: 500MB) 
├── logs-2025-10-15-01 (1am-2am: 450MB) ├── logs-2025-10-15-02 (2am-3am: 200MB) └── ... 

Query: "Show me failed logins from 2am-4am" 
→ Only scans logs-2025-10-15-02 and logs-2025-10-15-03 
→ Ignores other 22 hours of data
```

So in this case we reduce the indexing load by decreasing the size of our data set, rather than modifying our base query.

## Indexing Differences between SIEMs

### Splunk:

- Splunk uses proprietary TSIDX (Time Series Index) files.
- Buckets are sorted by heat.
	- **Hot** - actively writing data.
	- **Warm** - complete searchable data.
	- **Cold** - compressed, slower
	- **Frozen** - archived, offline.
- Bloom filters are used for fast negative lookups

### Elastic:

- Apache Lucene inverted indexes are used.
- Data is sharded - meaning it is kept across multiple servers for parallel processing
- Index templates define structure. Similarly to database schemas.

## Indexing Performance Factors:

**Fast Searches:** 
- Indexed fields (e.g., `source_ip="10.0.0.5"`) 
- Time-bounded queries (last 24 hours) 
- Wildcard at end (e.g., `user=admin*`) 

**Slow Searches:** 
- Non-indexed fields (e.g., searching raw log message)
- Open-ended time ranges (all time) 
- Leading wildcards (e.g., `user=*admin` forces full scan)
- Regex on large datasets 

**Why Indexing Performance Matters** 
- **Speed:** Query 1TB of logs in seconds 
- **Cost:** Compressed indexes use 10-30% of raw log size 
- **Scalability:** Add more index servers to handle more data