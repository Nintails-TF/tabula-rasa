---
title: 'Cookies (40):'
updated: 2022-10-19T18:01:40.0000000+01:00
created: 2022-10-19T17:16:32.0000000+01:00
---

Using WhatWeb we can get the IP of the website:
![image1](../../../../_resources/image1-32.png)

Then using nmap we can get details of what is running on the ports:
![image2](../../../../_resources/image2-30.png)

When you load the website, you briefly see a session cookie before it gets expired, If I was able to intercept that packet. I could input the session cookie.

We need to enter the default snikerdoole name, then we can enumerate through the cookie length, until we get to cookie = 18. Which gives us the flag.

