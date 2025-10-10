---
title: 'User Enumeration:'
updated: 2023-07-20T01:03:41.0000000+01:00
created: 2023-07-20T00:48:44.0000000+01:00
---

Introduction:

A key ability in enumerating a word press target is enumerating a list of valid users. If we can enumerate users we can guess default credentials or brute force password attack. If we succeed we can log into the Wordpress back end as an author or even admin.

We can then use this access to modify the website or interact with the webserver in some cases. We have two main methods of **manual enumeration**.

ID finder method:

Firstly, we can review created posts to figure out the ID assigned to users and their username - for example if we look at an admin post we can see a link to an admin profile.

***Generally, admins are assigned with a user ID of 1.***

We can check this by specifying the **author** id in a url:
<http://blog.inlanefreight.com/?author=1>

We can do this via cURL and find out that in the **HTTP repsonse** that the userID belongs to an **admin user:**
![image1](../../../../_resources/image1-127.png)

If the user doesn't exist. Then we will get a **404 not found error:**
![image2](../../../../_resources/image2-103.png)

JSON Method:

This method requires interaction with the JSON endpoint which enables us to obtain a list of users - **however, this only works on \<4.7.1 WordPress versions**. New versions of Wordpress only show if a user is configured or not, whilst the older versions give all user details of posts.

![image3](../../../../_resources/image3-83.png)

![image4](../../../../_resources/image4-67.png)
