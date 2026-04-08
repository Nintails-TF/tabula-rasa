---
date created: Wednesday, October 15th 2025, 2:56:50 pm
date modified: Wednesday, October 15th 2025, 2:57:06 pm
Parent Link: "[[../Academy Modules/Security monitoring and SIEM Fundamentals#Parsing|Parsing]]"
---

# Parsing Process:

**Pattern Matching** - SIEMs use regex-based or extended-regex to figure out what log format is being used
```json
Example Windows Event Log Parser:
EventID=(?<event_id>\d+) User=(?<user>\w+) Source=(?<source_ip>\d+\.\d+\.\d+\.\d+)

This extracts:
- event_id: 4624
- user: admin
- source_ip: 10.0.0.5
```

**Field Extraction** - The parsing module then pulls out specific values and labels them.
```json
Before Parsing (raw string):
"EventID=4624 User=admin Source=10.0.0.5"

After Parsing (structured data):
{
  "event_id": "4624",
  "user": "admin",
  "source_ip": "10.0.0.5",
  "timestamp": "2025-10-15T14:23:45Z",
  "log_source": "Windows Security"
}
```

**Type Conversion** - Data is then converted into specific types for further queries. 
```json
- "4624" (string) → `4624` (integer) for numeric searches
- "2025-10-15T14:23:45Z" (string) → `datetime` object for time-based queries
- "10.0.0.5" (string) → `IP address` type for network analysis
```

***
# Parsing in different SIEMs:

Your main SIEM tools can parse in different ways. Splunk differs from the Elastic Stack, but the core foundations are the same.

Parsing can be challenging because you can have a few different quirks:
- Multi-line logs.
	- *Java stack traces 50+ lines*
- Inconsistent formatting
	- *Different vendors and software versions*
- Custom applications
	- *Weird logging from homegrown apps.*
- Performance concerns.
	- *Having to parse millions of logs in an efficient manner.*