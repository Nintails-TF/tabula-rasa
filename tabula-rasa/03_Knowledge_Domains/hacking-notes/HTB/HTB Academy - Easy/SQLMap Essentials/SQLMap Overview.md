---
title: 'SQLMap Overview:'
updated: 2023-08-28T09:00:07.0000000+01:00
created: 2023-08-26T10:46:08.0000000+01:00
---

Introduction:

**SQLMap** is a FOSS penetration testing tool made in python, it automates the process of detecting and exploiting SQL injection flaws (SQLi) - it has been continuously developed since 2006 and is still maintained today.

**SQLMap** has a powerful detection engine, numerous features and a broad range of options and flags to fine tune the many aspects of it like:
![image1](../../../../_resources/image1-199.png)

We can install **SQLMap** simply using:
![image2](../../../../_resources/image2-165.png)

Supported Databases:

SQLMap supports a wide range of database environments to inject into, such as:
![image3](../../../../_resources/image3-130.png)

Supported SQL Injection Types:

SQLMap is one of the only tools which can detect and exploit **all known SQLi types**. We can check what is supported using the **sqlmap -hh** flag, we see that **BEUSTQ** is the default injection techniques to look for, in which BEUSTQ stands for:
![image4](../../../../_resources/image4-105.png)

Boolean-based blind SQL Injection:

This type of query exploits vulnerabilities through the differentiation of TRUE and FALSE query results, we can use this to get small chunks of information by deduction using true/false results. You can glean information such as:

- HTTP codes
- Page Titles
- Filtered Text
- Etc

**True** results generally are based on responses having none or marginal differences from normal server responses. **False** results are based on having substantial differences from the regular server response.

An example of a **Boolean-based blind SQL Injection:**
![image5](../../../../_resources/image5-81.png)

These SQL injections are the most common SQLi type in web applications.

Error-based SQL Injection:

If the **database management system** (DBMS) returns error as a part of the server response for database queries, then we can use these error results to carry information from queries, in such cases - we can use crafted payloads to target DBMS that is being used.

Commonly used DBMS like:
![image6](../../../../_resources/image6-58.png)

Are supported in **SQLMap**. An example of which is:
![image7](../../../../_resources/image7-51.png)

**Error-based SQL Injection**, is faster than all other queries - excluding UNION queries - since it can retrieve a chuck of data each request (e.g. 200 bytes).

UNION query-based:

With **UNION queries** we seek to extend the original **vulnerable** query, to include the injected statements results. What this means is that when the original query is rendered to the user, we can get addional results that can help.

This query is the fastest, since the attacker can even pull whole databases with a single request making these situationally very powerful.

An example of a **UNION based SQL injection:**
![image8](../../../../_resources/image8-44.png)

Stacked Queries:

Stacking SQL queries or also known as **piggybacking**, is the form of injection additional SQL statements after a vulnerable one. There often is a requirement for running non-query statements like **UPDATE, INSERT or DELETE.**

An example of a stacked query:
![image9](../../../../_resources/image9-37.png)

*Note that this feature isn't possible on all DBMS's - it must be supported like on MS SQL server and PostgreSQL which support stacked queries by default.*

These vulnerable queries can be used to execute OS commands and retrieve data like **time-based blind SQLi types.**

Time-based Blind SQL Injection:

The principle behind **Time-based blind SQL injections** is that similar to **Boolean-based blind SQL Injection**. However, we are using the response time of the query instead of **TRUE/FALSE.**

- **TRUE** responses are characterized by longer than regular response times.
- **FALSE** responses are characterized by normal server response times.

These queries are much slower than **Boolean-based blind SQL Injection** this is because the responses that are TRUE will delay the server response and this technique is normally used when **Boolean-based** queries cannot be used.

An example is:
![image10](../../../../_resources/image10-31.png)

For example in auxiliary functions (INSERT, DELETE, UPDATE), which are executed without changing the rendering of the query, we need to check response times since we cannot "see" the tables in the back-end.

Inline Queries:

Inline queries are uncommon and are a type of query that is embedded within the original query, SQLMap will still support and check for this however, an example of an inline query would be:

![image11](../../../../_resources/image11-24.png)

Out-of-band SQL Injection:

This type of SQLi attack is considered to be one of the more advanced types of SQLi, it is commonly used as a last resort, when other SQLi attacks are too slow or are unsupported. SQLMap supports out-of-band SQLi via **DNS exfiltration** in which requested queries are retrieved using DNS traffic.

We use the DNS server from the domain to request non-existant domains that contain the response we want to receive.

E.g. we have the TLD **attacker.com**, so we use **foo.attacker.com** where **foo** in the SQL response we want to receive.

Out-of-band SQL injections exploit the error messages from these DNS requests to form SQL responses.

An example of an **out-of-band SQL Injection:**
![image12](../../../../_resources/image12-18.png)

