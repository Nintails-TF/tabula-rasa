---
title: Proxying Tools
updated: 2023-08-11T11:23:34.0000000+01:00
created: 2023-08-11T10:22:47.0000000+01:00
date modified: Monday, May 13th 2024, 10:21:40 pm
---

Introduction:

An important part of using web proxies, is enabling the interception of web requests made by CLI tools. To route all web requests made thorough proxy tools, we need to setup proxy tools.

Why do we use proxies?:

A big reason why we care about using proxies, is that you can bypass blocks and bans, let's say your current IP blocks certain websites you want to access, then you can route your traffic through a proxy to access the same website.

Proxychains:

A very useful tool within Linux is **proxychains** which routes all traffic that comes from the command line, to any proxy we define. **Proxychains** is the simplest and easiest way to route traffic via our CLI.

To use proxychains, we need to edit our **/etc/proxychains.conf** file and comment out the final line and add the following:
![image1](../../../../_resources/image1-174.png)

We should also enable **quiet mode** in order to reduce any noise made by proxychains, now we can use proxychains via **pre-appending** proxychains to any command, for example using cURL:
![image2](../../../../_resources/image2-143.png)

We can see the proxychains line or look inside a web proxy to check that we have used the proxy correctly:
![image3](../../../../_resources/image3-109.png)

*In this case we are using **proxychains 3.1.***

Proxies via nmap:

We can also setup proxies via nmap using the **--proxies** flag - making sure to use the **-Pn** flag to also skip host discovery (since it is recommended by nmap when using proxies). Finally we can use the **-sC** flag to examine what the nmap scan is doing.

![image4](../../../../_resources/image4-86.png)

*Note that not all traffic is routed via nmap since the proxy tool is still in development, so it may be wise to still use the **proxychain** method here.*

Proxies in Metasploit:

Finally, we can also proxy web traffic via Metasploit modules. After starting metasploit, we can use the command **set PROXIES** flag to configure a proxy:
![image5](../../../../_resources/image5-66.png)

We can use proxies in most other applications and CLI tools, we just need to setup proxies - **then we can use web proxies to monitor what these proxies are doing and even modify them.**

*This is because we are sending the requests through our localhost so that the web proxy will pick the requests up*

Task - Looking at metasploit request:

Our task is to run a function in metasploit (auxiliary/scanner/http/http_put) and to monitor that request in BURP.

