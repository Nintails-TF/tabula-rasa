---
title: 'Service Scanning - Questions:'
updated: 2022-08-31T19:01:58.0000000+01:00
created: 2022-08-23T15:09:23.0000000+01:00
---

![image1](../../../../../_resources/image1-71.png)
Service Scanning - Questions:
23 August 2022
15:09
![image2](../../../../../_resources/image2-53.png)
Using a basic nmap scan:

![image3](../../../../../_resources/image3-45.png)
We know that at port 8080 the service **http-proxy** is running. But we don't know what version it is running. We can try *banner grabbing* it using netcat.
![image4](../../../../../_resources/image4-37.png)
This doesn't help us though.

Automating this via nmap we find that Apache tomcat is running:
![image5](../../../../../_resources/image5-27.png)

![image6](../../../../../_resources/image6-18.png)
![image7](../../../../../_resources/image7-15.png)
We need to use -sV to check for any non-default port configurations:

![image8](../../../../../_resources/image8-13.png)

We see that telnet is running on port 2323.
![image9](../../../../../_resources/image9-12.png)
Accessing the SMB:

![image10](../../../../../_resources/image10-10.png)

We then need to login as bob into the users share and get the flag prompt.

![image11](../../../../../_resources/image11-9.png)
We then use cd to navigate to the flag directory and get the file (note when we get the file, it is downloaded to the directory in which we started smbclient in).

