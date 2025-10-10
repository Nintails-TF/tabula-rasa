---
title: Active Infrastructure Identificatio
updated: 2023-08-03T17:10:48.0000000+01:00
created: 2023-08-02T09:14:06.0000000+01:00
date modified: Monday, May 13th 2024, 10:19:30 pm
---

Introduction:

A web app's infrastructure is what keeps it running - we always care about the **web server** that is running and discovering what type (Apache, Nginx, IIS, etc) and what version is running can be critical in further exploitation.

For example, if we find that **IIS** is running, we can deduce the version of windows that is running too - since we can map the Windows version to the version of the default IIS:

- IIS 6.0: Windows Server 2003
- IIS 7.0-8.5: Windows Server 2008 / Windows Server 2008R2
- IIS 10.0 (v1607-v1709): Windows Server 2016
- IIS 10.0 (v1809-): Windows Server 2019

This is **usually correct** when working with Windows. But in the case of Linux/UNIX distributions we cannot perform the same trick.

Web Servers:

We need to find as much info about the web server so we can understand its functionality and make adjustments. For example:

- URL rewriting functionality
- Load balancing
- Script engines used
- **Intrusion Detection Systems** in place
  - IDS can impede our testing actions.

*The first thing we can do is to look at the response headers, we check the response headers via BURP or CURL:*
![image1](../../../../_resources/image1-154.png)

- **X-Powered-By Header -** This tells us what the web app is powered by. We usually see values like *PHP, ASP.NET, JSP, etc.*
- **Cookies -** Cookies are ripe for exploitation usually. Default cookies can tell us what software is running:
  - **.NET: ASPSESSIONID\<RANDOM\>=\<COOKIE_VALUE\>**
  - **PHP: PHPSESSID=\<COOKIE_VALUE\>**
  - **JAVA: JSESSION=\<COOKIE_VALUE\>**

Whatweb usage:

Whatweb is useful because it is able to recognise many different web technologies like CMS, blogging platforms, statistic/analytic packages, JS libraries, web servers and embedded devices.

*It is important to look at the manual using **Whatweb -h** to understand what options to use.*

Mainly, knowing what aggression level do and verbose output.

**Wappalyzer** can do the same thing, all be it with less details, in a more streamlined result in a browser.

WafW00f:

WafW00f is a tool used to fingerprint **Web Application Firewalls** (WAFs) by sending requesting and analysing responses. We can install it via:
![image2](../../../../_resources/image2-125.png)

We can use the following flags:

- **-a** to check all possible WAFs in place, rather than stopping at the first match.
- **-i** to read targets from an input file.
- **-p** to proxy the requests.

Aquatone:

**Aquatone** is a tool used for automatic and visual inspection of websites across many hosts. It is very useful quickly gaining an overview of HTTP-based attacks. Aquatone does this via scanning ports, visiting websites and taking snapshots of them.

It is most important when dealing with huge sub-domain lists. Installing Aquatone can be done via:
![image3](../../../../_resources/image3-96.png)

We can now **pipe a subdomain list** and check aquatone:
![image4](../../../../_resources/image4-75.png)
*(by default a file named **aquaton_report.html** will be created, which contains the information).*

![image5](../../../../_resources/image5-58.png)

