---
title: 'Virtual Hosts:'
updated: 2023-08-05T03:55:17.0000000+01:00
created: 2023-08-05T02:57:06.0000000+01:00
---

Checking for Virtual Hosts:

We use fuzzing techniques in order to speed up the process of discovering virtual hosts. e.g.
![image1](../../../../_resources/image1-157.png)

Introduction:

A **virtual host** (**vhost**) is a feature that enables many websites to be hosted on a single server. We use virtual hosts to host many websites on a single web server.

The benefits of this is that by using virtual hosts you can save time and money by not needing to setup a new web server for each resource. We can also use this to create different websites for desktop and mobile devices.

The issue with vhosts, is that the processing power of the web server is shared. If one website is super popular and another is less popular, resource starvation can occur.

When we **implement virtual hosts** we can do so in two ways:

1.  *IP-based vhosting*
2.  *Name-based vhosting*

IP-based Virtual Hosting:

For this type, a host can have many IP addresses can be configured on each network or interface of a host. The servers or virtual servers running on the host can **bind** to one or more Ips.

What this means, is that different servers are accessed under different IP addresses on the host, from the **client's perspective** these servers are independent of each other.

Name-based Virtual Hosting:

We know that several domain names can refer to the same IP, for example: *admin.inlanefreight.htb* and *backup.inlanefreight* can refer to the same IP.

On the webserver, this means that both of these sub-domains are separated into different folders. For example:

- **Admin.inlanefreight.htb**
  - **/var/www/admin**
- **Backup.inlanefreight.htb**
  - **/var/www/backup**

In this event, we can see subdomains having the same IP address in **virtual hosts** or in different servers sitting behind a **proxy.**
