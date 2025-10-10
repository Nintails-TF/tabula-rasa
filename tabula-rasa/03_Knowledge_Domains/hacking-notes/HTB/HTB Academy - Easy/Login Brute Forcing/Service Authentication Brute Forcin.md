---
title: 'Service Authentication Brute Forcing:'
updated: 2023-08-17T13:15:00.0000000+01:00
created: 2023-08-16T16:51:52.0000000+01:00
---

SSH Attack:

The command used to attack a login service is fairly straightforward. We simply provide the **username** and **password** wordlists and add **service://SERVER_IP:PORT** at the end.

We need to include the -u (try all passwords on a single user first) and -f (stop once we have a successful login) flags too. **Hydra** will suggest to use **-t 4** flag to limit the number of **SSH** connection - this avoids us dropping connections, thus giving us a command of:

![image1](../../../../_resources/image1-187.png)
(Note that if performing this on HTB - use the port listed for the IP - NOT PORT 22).

Once we get a working pair, we can log into ssh:
![image2](../../../../_resources/image2-154.png)

Activity:
![image3](../../../../_resources/image3-119.png)

After we create the wordlists using cupp, we then can start the SSH brute force:
![image4](../../../../_resources/image4-95.png)
We get the creds **b.gates:4dn1l3M!\$** now we need to login using SSH:
![image5](../../../../_resources/image5-73.png)
And after we enter our password:
![image6](../../../../_resources/image6-50.png)

![image7](../../../../_resources/image7-43.png)

We simply repeat the FTP commands from above:
![image8](../../../../_resources/image8-37.png)

And we get the creds for the **ftp server**, m.gates:computer, now we log into the FTP server:
![image9](../../../../_resources/image9-31.png)

FTP Brute Forcing:

Once we are in, we can check other users on the system:
![image10](../../../../_resources/image10-25.png)

And we see that a user named m.gates is listed and we can try FTP brute force them:
![image11](../../../../_resources/image11-19.png)

*System admins sometimes test using different policies and tools, this means that sometimes tools are left installed on the system that shouldn't be.*

*Also we can use rockyou-10.txt for a smaller password list that only contains the top 92 passwords.*
![image12](../../../../_resources/image12-14.png)

After we get the password we can **FTP** as that user, or switch to them:
![image13](../../../../_resources/image13-13.png)
![image14](../../../../_resources/image14-10.png)

Switching example:
![image15](../../../../_resources/image15-7.png)

Downloading a FTP file:

1.  We get the flag
    1.  ![image16](../../../../_resources/image16-7.png)
2.  This file is downloaded to the remote machine:
    1.  ![image17](../../../../_resources/image17-6.png)
3.  Now we download the file to our machine
    1.  ![image18](../../../../_resources/image18-6.png)
    2.  This is how we can download files from a system using ssh.

