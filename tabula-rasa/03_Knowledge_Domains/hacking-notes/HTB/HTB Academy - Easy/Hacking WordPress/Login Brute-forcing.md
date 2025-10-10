---
title: 'Login Brute-forcing:'
updated: 2023-07-20T01:17:06.0000000+01:00
created: 2023-07-20T01:05:40.0000000+01:00
---

Introduction:

Once we have a list of valid users, we can then start a password brute force attack against the back-end. We should launch this attack via the **login page or xmlrpc.php page.**

If we POST the correct credentials into the xmlrpc.php, we receive the following response:

curl-X POST -d "\<methodCall\>\<methodName\>wp.getUsersBlogs\</methodName\>\<params\>\<param\>\<value\>admin\</value\>\</param\>\<param\>\<value\>CORRECT-PASSWORD\</value\>\</param\>\</params\>\</methodCall\>"http://blog.inlanefreight.com/xmlrpc.php
![image1](../../../../_resources/image1-128.png)

If the credentials are invalid we get a **403 Forbidden error:**
![image2](../../../../_resources/image2-104.png)

