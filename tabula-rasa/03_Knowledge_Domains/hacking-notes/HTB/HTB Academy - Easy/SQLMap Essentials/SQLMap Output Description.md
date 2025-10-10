---
title: 'SQLMap Output Description:'
updated: 2023-09-01T11:34:37.0000000+01:00
created: 2023-08-28T09:45:05.0000000+01:00
---

Introduction:

SQLMap can give us lots of information when we scan for SQLi vulnerabilities using it, it is paramount that we understand it so that we can properly report and manually exploit the vulnerability if needed, once SQLMap determines the type of injection and vulnerable parameter.

Understand Log Messages:

Common log messages includes:

**URL Content is stable:**
Log Message: "target URL content is stable"

*This means that there aren't any major changes between responses in continuous requests. If we have stable responses this means that it is easier to spot differences caused by SQLi attempts. **SQLMap** is able to deal with the "noise" of unstable targets - but stable targets are more ideal.*

**Parameter appears to be dynamic:**
Log Message: "GET parameter 'id' appears to be dynamic."

*We always want the tested parameter to be dynamic, this is because it is a sign that any changes to said value will result in a change in response. Thus this means that it is more likely to be linked to a database, if the output is **static** and does not change it could mean that the parameter isn't being processed.*

**Parameter might be injectable:**
Log Message: "heuristic test shows that GET parameter 'id' might be injectable (possible DBMS: MySQL)"

*DBMS errors are a good indication of potential SQLi, as SQLMap will send intentionally invalid values to indicate what DBMS system is being used (in this case MySQL) and shows that the target can be injected into.*

**Parameter might be vulnerable to XSS attacks**
Log Message: "heuristic XSS test shows that parameter 'id' may be vulnerable to Cross-site scripting attacks.

*Even though SQLMap primary purpose is to find SQLi vulnerabilities, a quick test is also ran on any possible XSS vectors, this can occasionally be the next step to follow if there aren't any SQLi-based attacks possible.*

**Back-end DBMS is "…":**
Log Message: "it looks like the back-end DBMS is MySQL. Do you want to skip other payloads for DBMSes?"

This is a handy feature we can use in a normal SQLMap run to try and narrow down a specific version of DBMS.

**Technique appears to be useable:**
Log Message: "ORDER BY' technique appears to be useable. This will reduce the time needed to find the right number of query columns. Automatically extending the range for current UNION query injection tests.

*Since we can use ORDER BY we can more quickly recognise the number of columns by conducting a binary search approach. This will speed up our UNION query searching.*

**Parameter is Vulnerable:**
Log Message: "GET parameter 'id' is vulnerable. Do you want to keep testing for others (if any)?"

*This is the most important message in SQLMap, since we only usually need a single injection point to mount an attack - however if we are performing a comprehensive pen test, we will need to state all attack vectors related to SQLi not just one method.*

More Log Message Explanations:

**Level/Risk values:**
Log Message: "For the remaining tests for MySQL, do you want to include all level 1 and risk values?"

*If we have a clear read on what DBMS is being ran, we can extend our scan beyond normal tests and we can run some SQL injection payloads - level 1 refers to the top level payloads.*

**Reflective Values Found:**

Log Message: "Reflective value(s) found and filtering out"

*This is a warning message that parts of the payload are found in the response, this can cause problem for automation tools as it is just junk, but SQLMap is smart enough to filter and remove the junk before displaying the original page content.*

**Parameter appears to be injectable:**

Log Message: "GET parameter 'id' appears to be 'AND Boolean-based blind - WHERE or HAVING clause' injectable (with --string="luther")"

*This indicates that our message is injectable, though this still can be a false-positive. In the case of **Boolean-blind** and **Time-blind** SQLi types there is a high chance of false-positives, SQLMap performs extensive testing for logic checks.*

*SQLMap has also found a constant string **luther.** This means we can use it to distinguish true and false responses. This removes the fuzzy comparison of responses and **cannot be considered a false-positive.***

**Time-based comparison statistical model:**
Log message: "time-based comparison requires larger statistical model, please wait…"

SQLMap uses a statistical model to compare regular and delayed responses. For this to work though, a sufficient amount of data needs to be gathered so SQLMap can determine delayed vs normal responses. Even if the web app has high latency.

**Extending UNION query injection technique tests:**
Log message: "automatically extending ranges for UNION query injection technique tests as there is at least one other (potential) technique found"

*UNION-based SQLi checks take much more requests for a successful recognition of useable payloads than other SQLi types. This is doubly so if the target appears to be non-injectable, the number of requests is capped to a constant value (i.e. 10).*

*If the target is vulnerable, SQLMap will extend the default number of requests for UNION query SQLi because of the higher chance of success.*

**SQLMap identified injection points:**
Log Message: "SQLMap identified the following injection point(s) with a total of 46 HTTP requests."

*After listing all injection points, we will get proof of how many exploitable SQLi vulnerabilities we have, do note that SQLMap only considers vulnerabilities which are provably exploitable - actually usable.*

**Data logged to text files:**
Log Message: "fetched data logged to text files under "home/user/www.example.com/"

*SQLMap will use the same log file after an initial run, this is to avoid sending excessive traffic and to store the sessions data.*
