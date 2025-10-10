---
title: Directory Indexing
updated: 2023-07-23T13:58:10.0000000+01:00
created: 2023-07-19T18:54:32.0000000+01:00
date modified: Monday, May 13th 2024, 11:05:05 pm
---

Introduction:

Active plugins are not the only areas of focus when we assess a WordPress website. ***Even if a plugin is deactivated - it still can be accessible** - thus if we can gain access to its associated scripts and functions. Deactivating a vulnerable plugin **isn't enough** the best practice is to remove or update unused plugins.*

![image1](../../../../_resources/image1-125.png)
*Fig 1. The disabled plugin - Mail Masta.*

For example, if we browse to the plugins director we can see that we still have access to Mail Masta:
![image2](../../../../_resources/image2-101.png)

**We can also do this using cURL:**

curl-s -X GET <http://blog.inlanefreight.com/wp-content/plugins/mail-masta/> \|html2text
![image3](../../../../_resources/image3-81.png)

This technique of looking inside plugin folders is called **directory indexing**. It allows to navigate through the folder and access files that can contain sensitive information or vulnerable code.

It is best practice to disable directory indexing on web servers so that attackers cannot gain access to any files or folders.
