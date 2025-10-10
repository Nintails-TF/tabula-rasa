---
title: "Static ain't always noise (20):"
updated: 2022-03-06T18:06:55.0000000+00:00
created: 2022-03-06T17:26:37.0000000+00:00
---

![image1](../../../../_resources/image1-27.png)
(chmod +x, makes a file an executable)
Making the file static and running it gives:
![image2](../../../../_resources/image2-25.png)

You can do the same thing with the ltdis.sh file:
![image3](../../../../_resources/image3-21.png)

Looks like we need to disassemble the static file using the ltdis.sh.
This gives us:

![image4](../../../../_resources/image4-15.png)

Opening the file gives us the flag:

![image5](../../../../_resources/image5-9.png)

