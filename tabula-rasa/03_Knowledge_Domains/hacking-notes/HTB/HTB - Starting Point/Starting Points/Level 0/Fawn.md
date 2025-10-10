---
title: Fawn
updated: 2022-07-26T18:32:27.0000000+01:00
created: 2022-07-24T18:13:17.0000000+01:00
---

What does the 3-letter acronym FTP stand for?:
*It stands for File Transfer Protocol. It operates in the application layer and it was first developed and used in 1971. It is a key part of the internet protocol suite (TCP/IP) that allows user to download files from other clients/servers.*

Which port does the FTP service listen on usually?

*FTP normally listens on port 21.*

What acronym is used for the secure version of FTP?

*The secure version of FTP is SFTP (Secure File Transfer Protocol) which uses SSH to transfer files.*

What is the command we can use to send an ICMP echo request to test our connection to the target?

*Simply a ping command can be used.*

From your scans, what version is FTP running on the target?

*Using nmap -sV, which checks for the version of what is running on the port we can see that FTP version "vsftpd 3.0.3" is running.*

![image1](../../../../../_resources/image1-53.png)

*We also know that it is a UNIX system.*

What is the command we need to run in order to display the 'ftp' client help menu?

*Ftp -h, but using man ftp seems to work for me and ftp -h doesn't work.*

What is username that is used over FTP when you want to log in without having an account?

*The username required is anonymous*

How do you log into a port using ftp?

![image2](../../../../../_resources/image2-39.png)

This gives us the flag:

![image3](../../../../../_resources/image3-32.png)

We can delete the file using rm.

![image4](../../../../../_resources/image4-24.png)

