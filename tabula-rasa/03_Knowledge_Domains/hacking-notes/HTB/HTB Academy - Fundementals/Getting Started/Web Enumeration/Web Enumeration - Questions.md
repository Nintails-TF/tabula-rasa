---
title: 'Web Enumeration - Questions:'
updated: 2022-09-10T19:57:52.0000000+01:00
created: 2022-09-04T14:55:37.0000000+01:00
---

![image1](../../../../../_resources/image1-73.png)

Using Curl we are able to find out that the server is running Apache.

![image2](../../../../../_resources/image2-55.png)

Using WhatWeb we find out that it is a US server with the title *HTB Academy.*

![image3](../../../../../_resources/image3-47.png)

Visiting the website reveals that it is a blog.

Admin Login:

Looking at the admin login page, we see an admin panel:

![image4](../../../../../_resources/image4-38.png)

Username and password credentials are then found within the source code:

![image5](../../../../../_resources/image5-28.png)

We then are presented with the flag:

HTB{w3b_3num3r4710n_r3v34l5_53cr375}
Using GoBuster:

Firstly, using a brute force attack method on the directories:

![image6](../../../../../_resources/image6-19.png)

Using the common.txt wordlist that is pre-packaged with kali we can see the following directories are available:

![image7](../../../../../_resources/image7-16.png)

We can see that .hta, .htpasswd and .htaccess are forbidden. But we are able to access index.php and robots.txt.

Robots.txt contains:-w
![image8](../../../../../_resources/image8-14.png)

Which shows us an admin login via php, lets now take a look at the php index file:
Which is the same as the main page.

Then we can check out the WordPress domain which reveals that WordPress is still in setup mode:

![image9](../../../../../_resources/image9-13.png)

