---
title: 'RCE using Theme Editor:'
updated: 2023-07-21T21:31:00.0000000+01:00
created: 2023-07-21T21:20:48.0000000+01:00
---

Attacking the back-end:

With admin access to WordPress we can modify the PHP source code to execute system commands, to perform this attack we need to:

1.  Log in with admin credentials.
2.  Go to **appearance**
3.  Go to **Theme editor**

This allows us to edit the PHP source code directly. We should choose an unused theme and then edit a non-critical file like the 404 page or **404.php.**
![image1](../../../../_resources/image1-134.png)

This allows us to execute system commands via GET this enables us to spawn a shell and get a web shell. We do this via a **cURL** command:

![image2](../../../../_resources/image2-109.png)

