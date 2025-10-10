---
title: Passive Infrastructure Identification
updated: 2023-08-02T09:13:46.0000000+01:00
created: 2023-08-02T08:49:28.0000000+01:00
date modified: Monday, May 27th 2024, 3:31:09 pm
---

Introduction:

There are other tools we can use to get info about servers without interacting with them, [**Netcraft**](https://sitereport.netcraft.com) is a valuable asset here. The most important details are:
![image1](../../../../_resources/image1-153.png)

A low hanging fruit you can sometimes grab, is that you can get the **latest IP used** and find the **actual webserver IP** and connect to it directly. This is because sometimes the IP is exposed before load balancers, WAFs and IDS are implemented.

Wayback machine:

The wayback machine is an internet archive that collects and digitizes materials for free using web crawlers. We can use the wayback machine to find old versions of websites. We can look at the old plugins and version that the website is using and try exploiting them.

This is valuable since often wp plugins end up being disabled rather than deleted so you can secure bounties this way.

We can use the command line utility of **waybackurls** to inspect URLs saved by the wayback machine, using the -dates flag we can look at URL that have been crawled by dates:

![image2](../../../../_resources/image2-124.png)

