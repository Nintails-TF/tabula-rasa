---
title: 'Attacking Tuning:'
updated: 2023-09-07T14:45:45.0000000+01:00
created: 2023-09-04T10:25:15.0000000+01:00
---

Introduction:

In most cases, SQLMap will normally work with default settings. However, there are options that can be configured in order to help SQLMap detect SQLi issues. Every payload sent to the target consists of:

- **Vector**
  - *The vector is the central part of the payload which holds the SQL code to be executed at the target destination.*
  - e.g. **UNION ALL SELECT 1, 2, VERSION()**
- **Boundaries**
  - *The boundaries refer to the prefex and suffix formations which are used for proper injection of the SQL statement into the database.*
  - e.g. **'\<vector\>-- -**

Prefix and Suffix:

Sometimes, we may need to use specific prefixes/suffixes in order to inject into the DBMS. In this case, we use the **--prefix** and **--suffix** flags as followed:
![image1](../../../../_resources/image1-204.png)
kali
What this will do is wrap any vector values with the prefix and suffix, For example if we have the following PHP code:
![image2](../../../../_resources/image2-170.png)

So our vector of: **UNION ALL SELECT 1,2,VERSION() - would become: "%'))UNION ALL SELECT 1,2, VERSION()-- -".** The full SQL statement consists of:
![image3](../../../../_resources/image3-135.png)

Level and Risk:

By default, SQLMap uses the most common prefix/suffix boundaries. Along with vectors that have a high chance of success on a vulnerable target. However if the target appears to be unaffected, a larger set of attack vectors can be enabled by using risk/level options.

- The **--level** flag (1-5, default 1) extends both vectors and boundaries that are being used based on how likely they are to succeed.
- The **--risk** flag (1-3, default 1) extends the use vector based on the risk of causing problems to the target. i.e. risk of database entry loss or DOS (Denial-Of-Service).

You can check the level and risk of each payload by using a **verbosity level** of 3 or higher, which will highlight what payloads are being used:
![image4](../../../../_resources/image4-110.png)

The number of payloads increases greatly as you increase level and risk. By default (--level=1, --risk=1) we have **72 payloads for each parameter.** In the most detailed attack (--level=5, risk=3) we have **7,865 payloads for each parameter.**

AS SQLMap is already configured to check the most common boundaries, we generally don't need to configure risk of level options - since the will make the scan much slower. *However; in special cases we may need to configure these options* - usually in the case of OR payloads.

Using **OR payloads** are dangerous because they have the potential to actively modify database content - though uncommonly - using **UPDATE or DELETE** queries.

Advanced Attack Tuning:

We can further fine tune our attacks using various flags and options. SQLMap will not use these flags by default, so we should be familiar with them just in case we need to use them.

**Status Codes:**
*When we are dealing with lots of dynamic content, we can use the differences between **true** and **false** responses to detect certain webpages. e.g. **200** for **TRUE** and 500 for **FALSE.** The option **--code** can be used to fix the definition of what is true to a HTTP status code. (--code=200).*

**Titles:**
*Sometimes we can see changes in response by looking at page titles. We can use the flag **--titles** to instruct SQLMap to detect using comparisons in titles.*

**Strings:**
*In the case of specific string values appearing in **TRUE** responses, whilst being absent in **FALSE** responses, we can use the **--string option**. We can fixate detection based on an appearance of a particular string. (e.g. **--string=success).***

**Text-only:**
*When we are dealing with lots of hidden content with certain HTML tags like \<script\>, \<style\>, \<meta\>, etc. We can use the text-only switch which will perform comparison statements on all **visiable/textual** content. (e.g. --text-only)*

**Techniques:**
*Sometimes, we need to narrow down what payloads we are using against a target. For example, if **time-based blind payloads** are cause problems in a form due to timeouts or if we need to force the usage of a specific SQLi payload type.*

*We would use **--techniques=BEU.** Which would perform **Boolean-based blind, error based and UNION-query payloads** but would skip time-based blind.*

**UNION SQLi Tuning:**

In some cases, **UNION SQLi payloads** require user-provided information to work - if we can manually find the number of columns in the vulnerable query we can provide SQLMap with the flag of **--union-cols=17**.

We can also filter using dummy values if the default SQLMap **NULL** and Random integers don't work on the current table, we set **union-char.** (e.g. **--union-char='a'**).

Finally, in the even there is a requirement to use an appendix at the end of a UNION query in the form of **FROM \<table\>** - this is the case in **Oracle** DBMS - we use the option **--union-from.** (e.g. **--union-from=users**).

