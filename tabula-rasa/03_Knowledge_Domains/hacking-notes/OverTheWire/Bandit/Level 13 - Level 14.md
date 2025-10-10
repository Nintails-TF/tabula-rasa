---
title: Level 13 -> Level 14
updated: 2022-10-18T22:59:19.0000000+01:00
created: 2022-10-18T22:51:45.0000000+01:00
---

We get an SSH private key and we need to connect to the next level using it. You could exfiltrate the file using a FTP of some kind, or you could just manually copy the file into an empty file made using touch.

![image1](../../../_resources/image1-224.png)

You need to chmod the permissions to be 600, otherwise you get the error:
![image2](../../../_resources/image2-190.png)

Then, you can connect to the next level, you are getting there, bit by bit.

