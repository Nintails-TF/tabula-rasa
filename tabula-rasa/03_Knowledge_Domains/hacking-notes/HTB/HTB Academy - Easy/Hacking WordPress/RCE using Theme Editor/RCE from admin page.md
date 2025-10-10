---
title: 'RCE from admin page:'
updated: 2023-07-21T22:57:44.0000000+01:00
created: 2023-07-21T21:39:15.0000000+01:00
---

Using the web shell:

We need to place our commands in the cURL string to navigate to the correct directory and then to cat the contents of the file:

We want to execute the command:
**cd /home/wp-user/ \| cat flag.txt**

cd+/home/wp-user/+\|+cat+flag.txt

I'm on the RCE part of the hacking WordPress module - I've uploaded a webshell to the target, but I can't seem to change directory at all, so access the "wp-user" directory and cat the flag.txt file.

/usr/src/wordpress/wp-content/themes/twentynineteen

![image1](../../../../../_resources/image1-135.png)

![image2](../../../../../_resources/image2-110.png)

**YOU CANNOT PIPE COMMANDS OR CD IN A FUCKING WEBSHELL FOR SOME REASON**

![image3](../../../../../_resources/image3-86.png)

Once we login we can access the Theme Editor:
![image4](../../../../../_resources/image4-68.png)

Then we can modify a non-essential file and navigate to it using cURL:
![image5](../../../../../_resources/image5-53.png)

Since the ID command executed, this means we have a web shell.
