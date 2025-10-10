---
title: 'Skills Assessment:'
updated: 2023-07-31T18:53:15.0000000+01:00
created: 2023-07-30T22:12:32.0000000+01:00
---

Fuzzing Websites:

- The **archive and faculty sub-domain** which has a directory named **courses.**
  - Both of which have an empty index.php file.
- There is a server status page which we don't have access to.

***Our roadblock here, was not using a comprehensive enough wordlist to scan everything - using common wasn't enough.** We should perform a more comprehensive scan on the /course/ sub-directory.*

The page we care about is: <http://faculty.academy.htb:54961/courses/linux-security.php7>

Parameter Fuzzing:

Now that we have a page that we care about, we can start parameter fuzzing the page to try gain access to it. **Let's first try the GET method of parameter fuzzing:**
![image1](../../../../_resources/image1-148.png)
![image2](../../../../_resources/image2-120.png)

Now let's enumerate using the POST method:
![image3](../../../../_resources/image3-93.png)
![image4](../../../../_resources/image4-72.png)

So we now have the parameters of: **user and username.** So we should start to value fuzz these.
![image5](../../../../_resources/image5-55.png)
![image6](../../../../_resources/image6-36.png)
We first tried using a smaller username wordlist, then we found our result early in a big username wordlist.

We can now CURL to this page and get the flag:
![image7](../../../../_resources/image7-30.png)

HTB{w3b_fuzz1n6_m4573r}
Introduction:

Given an online academy's IP address - locate all pages and domains linked to their IP and enumerate their IP properly - **this is the important first step in a penetration test**.

Starting out:

First we add the DNS to our hosts file:
![image8](../../../../_resources/image8-26.png)

We then can start to fuzz the VHOSTS to get access to hidden sub-domains:
![image9](../../../../_resources/image9-22.png)

*This returns every word and the wordlist as having a website, so we need to use the flag **-fs 985** to remove fake results:*
![image10](../../../../_resources/image10-17.png)

We now know that there are 3 sub domains:

1.  *Archive.academy.htb*
2.  *Test.academy.htb*
3.  *Faculty.academy.htb*

***We need to add all of these to our etc/hosts file:***
![image11](../../../../_resources/image11-12.png)

Testing for file extensions:

Before we start to fuzz the sub-domains we should take a look at what file extensions are accepted.
![image12](../../../../_resources/image12-8.png)

We check all the domains and find that:
![image13](../../../../_resources/image13-7.png)
**(We do include phps even though we don't have access to it - it is forbidden - it still exists on the web server).**
