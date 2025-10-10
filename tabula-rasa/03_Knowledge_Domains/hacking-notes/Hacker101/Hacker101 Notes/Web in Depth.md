---
title: Web in Depth
updated: 2022-08-03T17:49:51.0000000+01:00
created: 2022-08-03T12:14:47.0000000+01:00
date modified: Monday, May 13th 2024, 10:59:39 pm
---

Web in Depth:
[Hacker101 - The Web In Depth](https://www.youtube.com/watch?v=DWBUQiaN5ZM&t=1s)

![image1](../../../_resources/image1-234.png)
03 August 2022
12:14
Requests:

The main form of requests are:
![image2](../../../_resources/image2-192.png)

The request headers that are commonly used are the following:

- **Host** - Indicates the desired host handling the request
- **Accept** - Indicates what MIME (Multipurpose Internet Mail Extensions) type(s) are accepted by the client, commonly used for JSON or XML output for web services (APIs, etc)
  - So you can edit requests and get an XML output from a page.
- **Cookies** - Passes cookie data to the server
- **Referrer** - Page leading to this request (is not passed to other servers when using HTTPS on origin)
- **Authorization** - Used for *basic auth pages* (usually)*.* Takes the form of *Basic \<base64'd username:password\>*
  - You can easily decode the base64 string though using a decoder.

Cookies:

Cookies are key-value pairs of data that are sent from the server and reside on the client for a fixed period of time. Sometimes these periods can be very long.

Each cookie has a domain pattern that it applies to and they are passed with each request the client makes to matching hosts. Sometimes cookies are in scope for root or a specific sub-domain. Meaning you can send cookies to domains in which they aren't meant to be sent to.

