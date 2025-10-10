---
title: WP Core Version Enumeration
updated: 2023-07-19T18:20:05.0000000+01:00
created: 2023-07-19T17:38:34.0000000+01:00
date modified: Monday, May 13th 2024, 11:07:22 pm
---

Introduction:

An essential part of enumeration is finding the **software version number**. The reason why this is key is for a multitude of reasons:

- Trying out default credentials.
- Searching for public vulnerabilities.
- Searching for out of date software.

We have various ways of doing this.

Viewing page source in browser:

1.  We can right-click on the browser and view the page source.
    1.  We can also use **CTRL + U** to directly view the page source.
2.  We can then search the source code by looking for the **meta generator** tag using **CTRL + F**.
    1.  Use **meta name filter**
        1.  ![image1](../../../../_resources/image1-123.png)

Using Grep:

We can perform a similar task using cURL and grep.

1.  We can get the website using cURL and then pipe the output to grep and to look for said meta tag
![image2](../../../../_resources/image2-99.png)

***We can also look for CSS and JS versions to infer the version number.***
