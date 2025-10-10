---
title: Connecting to HTB
updated: 2022-07-24T18:13:13.0000000+01:00
created: 2022-07-24T17:07:39.0000000+01:00
date modified: Tuesday, May 14th 2024, 6:16:17 pm
---

To connect to a machine on HTB you need to use a VPN service provider.
Download a vpn file, then run it using:

![image1](../../../_resources/image1-51.png)

Connecting to a machine:

Simply, connect using openVPN and make sure there is tun0, as the tuns don't work. Personally I've been using TCP (Transmission Control Protocol) rather than UDP (User Datagram Protocol) and that has had more success.

TCP is slower but is more reliable. UDP is faster but less reliable.
