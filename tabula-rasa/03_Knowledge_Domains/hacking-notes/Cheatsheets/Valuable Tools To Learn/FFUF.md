---
title: FFUF
updated: 2023-08-06T23:46:12.0000000+01:00
created: 2023-07-22T18:24:12.0000000+01:00
date modified: Monday, May 13th 2024, 10:47:25 pm
---

Basic Usage:

Select a wordlist using -w, you can get a decent wordlist from SecLists. **Other wordlists include assetnote.**
Supply a URL using -u, replace the area you want to fuzz with FUZZ, e.g.
![image1](../../../_resources/image1-19.png)

Filtering by size:

Sometimes you will want to filter by size. Using -fs (-f for filtering, -s for size).

Types of requests:

- We can perform POST requests using -d
- We can perform HTTP requests using -X

Optional flags:

- We can use -t to limit thread usage
- We can use -rate to limit our rate (requests per second)
- We can define -H to inject a header and -b to inject cookie values
  - This can be useful during testing, so people know you are a tester.

Recursive fuzzing:

Using the -recursion keyword, will look in all directories in which everything is found. We can also set the depth using -**recursion-depth.** -r means that we follow redirects
