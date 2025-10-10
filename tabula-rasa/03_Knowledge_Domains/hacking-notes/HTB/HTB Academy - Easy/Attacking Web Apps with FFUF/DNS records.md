---
title: DNS records
updated: 2023-07-25T15:09:55.0000000+01:00
created: 2023-07-25T12:20:44.0000000+01:00
date modified: Monday, May 13th 2024, 11:01:10 pm
---

Accessing domains:

Once we access the blog, we get the message that **Admin Panel moved to academy.htb.** If we try to visit that website we can't connect to the web-server.

This is because the website is not public - browsers only understand IP addresses - when we provide browser with a URL it checks the public DNS system and our **/etc/hosts** file. If the URL isn't in either then our browser cannot "find" the website.

Since **academy.htb** isn't inside our **/etc/hosts** file and isn't on the public DNS (i.e. google dns 8.8.8.8) it will fail to connect. So we need to add the domain to our **/etc/hosts** file - we can do this quickly using:

![image1](../../../../_resources/image1-143.png)
Sudo sh -c 'echo "94.237.56.76 admin.academy.htb" \>\> /etc/hosts'

We then can verify that this is domain maps to the IP we have been testing by visiting the same sites.
Fuzzing the new domain:

When we ran our tests on the IP, there was no info on **admin** or **admin panels** even when we did a big recursive scan. Now that we have the domain, **we start to look for sub-domains that fall under \*.academy.htb** to see if we can find anything.
