---
title: 'Nibbles Foothold:'
updated: 2022-12-20T09:12:04.0000000+00:00
created: 2022-12-19T12:39:29.0000000+00:00
---

![image1](../../../../../_resources/image1-84.png)

We can test that the PHP upload works using the id check, after uploading the shell.php file to the image plugin, we can check its folder:
![image2](../../../../../_resources/image2-66.png)

This shows:
![image3](../../../../../_resources/image3-57.png)

Which means we can execute PHP code and get a reverse shell.
Reverse Shell:

1.  First, edit the shell.php file to include a one-liner bash shell.
    1.  ![image4](../../../../../_resources/image4-48.png)
    2.  Attacking IP should be your tun0 ip
    3.  Listening port should be any port for out netcat listener
2.  Start a Netcat listener on your terminal.
    1.  ![image5](../../../../../_resources/image5-37.png)
3.  CURL or browse to it and execute it
    1.  You'll know if it works, since you get shell quickly.
4.  Upgrade our reverse shell to make it easier to use
    1.  ![image6](../../../../../_resources/image6-27.png)
    2.  If python2 doesn't work try the same command with python3.

We get two files when we are inside home/nibbler, the flag user.txt and a zip file that contains a shell script named monitor.sh

