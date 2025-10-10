---
title: Attacking WP using Metasploit
updated: 2023-07-22T01:19:12.0000000+01:00
created: 2023-07-22T01:14:19.0000000+01:00
date modified: Monday, May 13th 2024, 11:05:03 pm
---

Introduction:

Alternatively, we can also use the **Metasploit Framework (MSF)** to obtain a reverse shell on the target automatically. This does require an account that has rights to creates files on the webserver.

We can start MSF using ***msfconsole.*** What we want is the **wp_admin_shell_upload** module. We can search this via:
![image1](../../../../_resources/image1-136.png)

We then can use the **options** command to look at all the possible options:
![image2](../../../../_resources/image2-111.png)

Example Configuration:

We need to use the set command to make the required modifications, then we can use run to execute the module:
![image3](../../../../_resources/image3-87.png)

