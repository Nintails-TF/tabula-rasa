---
title: 'Web Enumeration:'
updated: 2022-09-04T14:55:26.0000000+01:00
created: 2022-08-31T18:33:07.0000000+01:00
---

Status Codes:

When you send a request using HTTP (or HTTPS) a server issues a **status code** which indicates what has happened to the client's request, There are 5 classes of codes:

- **1xx -** informational response: the request was received, continuing process
- **2xx -** Successful: the request was successfully received, understood and accepted
- **3xx -** redirection: further action needs to be taken in order to complete the request
- **4xx -** client error - the request contains bad syntax or cannot be fulfilled.
- **5xx -** server error - the server failed to fulfil an apparently valid request.

Common status codes include:

200 - OK: The request was successful
301 - Moved Permanently: The requests are directed to a target URI. (redirection)
403 - Forbidden: The server is refusing action on a valid request (User doesn't have privileges or authentication).

<https://en.wikipedia.org/wiki/List_of_HTTP_status_codes>

Web Enumeration Tips:

How should you go about web enumeration on web resources?

1.  Banner Grabbing
As discussed earlier, Banner Grabbing can be used to check if web servers are misconfigured. Using cURL we can retrieve server header information in the command line.

![image1](../../../../_resources/image1-72.png)

Another tool that is helpful is EyeWitness, which is used to take screenshots of target web apps, fingerprint them and identify possible default credentials.

2.  WhatWeb
WhatWeb can extract the version of web servers, supporting frameworks. This helps us pinpoint the technologies in use and help us search for vulnerabilities.

![image2](../../../../_resources/image2-54.png)

3.  Certificates
SSL/TLS certificates also are another potentially valuable source of information if HTTPS is in use. Viewing the certificate could reveal emails or company names, which can be used in phishing attacks.

4.  Robots.txt
It is common for webpages to contain a robots.txt file that instructs search engine web crawlers which resources can and cannot be used for indexing. Often we are able to find sensitive info by looking in this file like private files and admin pages.

5.  Source Code
We should also look at the source code of a webpage and check if there are any comments or additional information that can open up attack vectors.

Web enumeration is extremely important, as when scanning for services we run into services running on ports 80 (HTTP) and 443 (HTTPS). These are considerable attack areas that are ripe for exploitation if services are not exposed and services are patched and protected.

Directory Enumeration:

It is worth checking if any we can uncover any hidden files or directories on a web server that is not intended for public access. We can use GoBuster to perform directory enumeration, sometimes we can find hidden functionalities or pages that expose sensitive data that can be used to further access the web app.

GoBuster is also able to perform DNS, vhost and directory brute-forcing. There are also additional features, but these are the barebones we are interested in.

For a brute force attack in this case, we need a wordlist that can check for lots of different address names.

WordPress is an extremely common CMS (Content Management System) and it powers 34% of all websites on the internet, because of this it has a huge potential attack surface. Whilst WordPress is in setup mode, RCE can be achieved.

DNS Subdomain Enumeration:

Subdomains can contain essential resources like admin panels or applications that are exploitable, using GoBuster we are able to enumerate subdomains of a given domain using the dns flag to specify a DNS mode.

[SecLists](https://github.com/danielmiessler/SecLists) many useful lists to help us search for sub-domains.

![image3](../../../../_resources/image3-46.png)

