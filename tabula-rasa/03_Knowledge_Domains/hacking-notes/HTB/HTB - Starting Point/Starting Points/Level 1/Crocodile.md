---
title: 'Crocodile:'
updated: 2022-09-10T20:16:20.0000000+01:00
created: 2022-09-10T12:52:55.0000000+01:00
---

What nmap scanning switch employs the use of default scripts during a scan?

*-sC is used to scan using default nmap scripts. Some of these scripts are intrusive and shouldn't be ran without permission and could get flagged by some kind of monitoring software.*

What service version is found to be running on port 21?

*Using nmap we figure out that* vsftpd 3.0.3 is running (ftp), that allows anonymous login. On port 80 there is also Apache httpd 2.4.41 ((Ubuntu)) running.

What FTP code is returned to us for the "Anonymous FTP login allowed" message?

*230, which means - **User logged in, proceed. Logged out if appropriate.***

What command can we use to download the files we find on the FTP server?

*We can use the **get** command.*

What version of Apache HTTP Server is running on the target host?

*We know that* Apache httpd 2.4.41 ((Ubuntu)) is running on port 80.

What is the name of a handy web site analysis plug-in we can install in our browser?

*We can use [Wappalyzer](https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/)*

What switch can we use with GoBuster to specify we are looking for specific filetypes?:
*Using man on GoBuster dir, we can use **-x** to search for specific file extensions.*

What file have we found that can provide us a foothold on the target?

*The login.php file found using GoBuster can be used to get a foothold.*
Getting the flag:

Using FTP we can connect to the ftp share. This shows us two files:

![image1](../../../../../_resources/image1-58.png)

Inspecting these files reveals:

Usernames:

- aron
- pwnmeow
- egotisticalsw
- admin
Passwords:

- root
- Supersecretpassword1
- @BaASD&9032123sADS
- rKXM59ESxesUFHAd

Then using GoBuster we find php pages that we are able to login to:

![image2](../../../../../_resources/image2-43.png)

![image3](../../../../../_resources/image3-36.png)

We can try the login page using our credentials we found.

The admin username using the password rKXM59ESxesUFHAd worked:

![image4](../../../../../_resources/image4-28.png)

c7110277ac44d78b6a9fff2232434d16
