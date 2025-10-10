---
title: Understanding FFUF
updated: 2023-08-12T12:57:48.0000000+01:00
created: 2023-07-25T09:02:13.0000000+01:00
date modified: Monday, May 13th 2024, 10:50:49 pm
---

Introduction:

We can look at the ffuf help by using **ffuf -h** and we get a myriad of options, but the key flags are:
![image1](../../../../_resources/image1-140.png)

Directory Fuzzing:

When starting to fuzz, we use the flag **-u** for the URL and **-w** for the wordlist(s). The basic syntax for this is:
![image2](../../../../_resources/image2-113.png)

FFUF is really fast, it can test 90k URLs in roughly 10 seconds, however the speed is effected by your internet speed and ping - regardless it is fast. We can further increase speed by using the **-t** flag to increase the number of threads we want to (e.g. -t 200).

However, scanning using very high thread usage can cause an unintentional **DOS** (Denial of service) attack and degrades services of especially smaller more remote sites. You can even cause your own internet to go down in extreme cases.

**When we get an empty page**, we can see that the directory doesn't have a dedicated page, but that we do have access to it.

Fuzzing Example:
![image3](../../../../_resources/image3-89.png)
*(Remember to include the http:// portion - otherwise every fuzz attempt will be an error.)*

Output:
![image4](../../../../_resources/image4-70.png)

