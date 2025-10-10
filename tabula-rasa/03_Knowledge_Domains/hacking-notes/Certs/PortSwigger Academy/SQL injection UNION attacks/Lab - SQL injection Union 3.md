---
title: 'Lab - SQL injection Union 3:'
updated: 2023-06-04T15:17:48.0000000+01:00
created: 2023-06-04T12:45:36.0000000+01:00
---

![image1](../../../../_resources/image1-9.png)

Since we know exactly where the bug is located (product category filter), we can supply the following query to show all passwords from user with:

![image2](../../../../_resources/image2-8.png)

This gives us the following response:
![image3](../../../../_resources/image3-6.png)

Thus the creds:

***Administrator:odsua0aw6w5x2w1eq8wq  
wiener:3kit9rrrtu3l72smfwml***
***Carlos:3lz7c4qdklc8b7f6a8m7***
We can use these to login as admin.
![image4](../../../../_resources/image4-4.png)

The lab is solved.
