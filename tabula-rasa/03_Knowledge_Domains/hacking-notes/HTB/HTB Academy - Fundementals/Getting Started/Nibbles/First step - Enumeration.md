---
title: 'First step - Enumeration:'
updated: 2022-12-31T17:48:16.0000000+00:00
created: 2022-12-18T20:06:01.0000000+00:00
---

The first thing we need to do to attack a machine/target is to **enumerate** and to gather information, in this example, we are given the following information:
![image1](../../../../../_resources/image1-80.png)
Ippsec video:
<https://www.youtube.com/watch?v=s_0GcRGv6Ds>
Walkthrough:
<https://0xdf.gitlab.io/2018/06/30/htb-nibbles.html>

Since we already have walkthroughs and guides, this is a **grey box** exercise, since we do have information on the underlying systems. Most active machines, or real world machines will be **black box** exercises and would require deep reconnaissance.

Scanning for scripts:

We can normally scan for scripts using **-sC** with nmap. These scripts can be intrusive and can potentially trip alarms, so we can limit unnecessary traffic by only scanning the open ports, using **-p \[port number(s)\]**:
![image2](../../../../../_resources/image2-62.png)

In this case we can use the script **http-enum** which works by enumerating directories of popular web applications and servers:
![image3](../../../../../_resources/image3-54.png)

Whenever you are stuck on a problem with nmap or another tool, it is a good idea to look at the [documentation](https://nmap.org/)
Nmap:  

A great tool in our box for enumeration is using **nmap,** we can perform quick or deep scans. Important options are:

- **-sV:** This will scan the top 1000 ports.
- **-p-:** This will scan all 63,535 ports
  - You can run this in the background or in a separate tab whilst we do something else, since it takes a long time to complete.
- Using the **--open** flag we can return only open ports
- Using **-v** (verbose output) **-oG -** (greppable format)
- **-oA** writes the scan to an XML output, a greppable output and a text output.

For example:
![image4](../../../../../_resources/image4-45.png)

The importance of logging:nmap

Note that **-oA** is really important! Since we may need this scan information in a report; as it ensures that no evidence is lost and it keeps time-stamped logs of scanning and exploitation. Which can explain an outage or incident to a client who may need info about our activities.

Netcat:

We can do some banner grabbing, to confirm the info from nmap, port 22 tells us there is an Apache web server running Open SSH:
![image5](../../../../../_resources/image5-34.png)

Looking at port 80, we see that a http (web) server is running:
![image6](../../../../../_resources/image6-24.png)
