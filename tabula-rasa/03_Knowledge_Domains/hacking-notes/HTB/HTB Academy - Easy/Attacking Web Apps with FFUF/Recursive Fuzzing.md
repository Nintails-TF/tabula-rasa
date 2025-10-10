---
title: Recursive Fuzzing
updated: 2023-07-25T12:20:24.0000000+01:00
created: 2023-07-25T11:22:25.0000000+01:00
date modified: Monday, May 13th 2024, 10:50:01 pm
---

Why do we need recursive fuzzing:

Recursive fuzzing enables us to check all subdirectories, it is important when we have multiple directories each of which having subdomains and files that we can speed up the process.

When we scan recursively, another scan is automatically started when a new directory is found and new pages are fuzzed until the main website and all of its subdirectories are fuzzed. Some website have large sub-directories (e.g. /login/user/content/uploads/...etc). This will make the tree very large and take forever to execute.

We can solve the problem of cumbersome fuzzes by limiting the **depth** of the recursion, so that we only scan the first or second level of directories, so we can then focus on the most interesting directories and scan them deeply.

Scanning Recursively:

In ffuf we enable recursion, using the **-recursion** flag and we limit depth using **-recursion-depth**. If we specify a depth of 1, we will only look inside main directories and their direct children. During recursion we can also define an extension using the **-e** flag (e.g. -e .php).

*Importantly, we can use the **-v** flag to output full URLs - otherwise it can be difficult to tell which php file is in the directory.*

Recursion Example:

ffuf -w /usr/share/wfuzz/wordlist/general/common.txt -u <http://94.237.59.206:51229/FUZZ> -recursion -recursion-depth 1 -v -e .php

After performing recursion on the highest level domain, we can see that there are a few more index and home files located within **blog** and **forum:**
![image1](../../../../_resources/image1-142.png)

We fuzz using the common.txt file and:

*ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u <http://94.237.59.206:51229/FUZZ> -v -recursion -recursion-depth 1 -e .php*

*We find the flag:*
![image2](../../../../_resources/image2-115.png)

