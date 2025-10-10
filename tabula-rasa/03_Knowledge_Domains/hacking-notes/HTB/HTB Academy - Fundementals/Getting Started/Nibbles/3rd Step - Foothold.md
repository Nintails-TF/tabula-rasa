---
title: 3rd Step - Foothold
updated: 2022-12-19T12:38:27.0000000+00:00
created: 2022-12-19T11:25:55.0000000+00:00
date modified: Tuesday, May 14th 2024, 12:56:19 pm
---

Now that we have access to the admin portal, we need to transmute this into *code execution* and *reverse shell.* We can use **Metasploit** for this, but giving our admin mortal another enumeration for attack is a good idea.

We have the following options:
![image1](../../../../../_resources/image1-83.png)
The Plugin page definitely seems like the most juicy.

Abusing Plugins:

We can use the My Image plugin, to try and upload a snippet of PHP code, to test if we have code execution:
![image2](../../../../../_resources/image2-65.png)

We can upload this as a PHP file (*shell.php)* to check if we have code execution:
![image3](../../../../../_resources/image3-56.png)

We then can check the *content* directory for our image using **curl:**
![image4](../../../../../_resources/image4-47.png)

It has worked! And it shows us the **nibbler** user context, meaning we can execute arbitrary PHP code on the server.
Getting a reverse shell:

We can now edit our PHP file to have commands that allow us to get a reverse
Shell. We can use the cheat sheet in [payloadAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md) to get PHP code for a reverse shell.

![image5](../../../../../_resources/image5-36.png)

In which:
- ATTACKING IP - the tun0 IP
- LISTENING PORT - a port of our choice for our Netcat listener.

This gives us our 1-liner of:
![image6](../../../../../_resources/image6-26.png)

Next we start a **Netcat** listener on our machine:
![image7](../../../../../_resources/image7-21.png)

Finally, we can **curl** to the image page (<http://nibbleblog/content/private/plugins/my_image/image.php>) again, or browse to it to execute a reverse shell:
![image8](../../../../../_resources/image8-19.png)

Upgrading our reverse shell:

Now that we have a reverse shell, we can upgrade it to make it nicer to work with.
We can use a python 1-liner for this:

![image9](../../../../../_resources/image9-18.png)

Since the server has python3, we can get a friendlier shell using the same command with **python3 -c …**

This gives us the flag and a zip file:
![image10](../../../../../_resources/image10-13.png)
