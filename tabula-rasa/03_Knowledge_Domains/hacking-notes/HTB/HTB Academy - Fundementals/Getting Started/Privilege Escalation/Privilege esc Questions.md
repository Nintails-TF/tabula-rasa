---
title: 'Privilege esc Questions:'
updated: 2022-10-18T19:16:19.0000000+01:00
created: 2022-10-18T15:31:10.0000000+01:00
---

![image1](../../../../../_resources/image1-78.png)

We log into the server:
![image2](../../../../../_resources/image2-60.png)

Using **sudo -l:**
![image3](../../../../../_resources/image3-52.png)
(User 1 doesn't have root privileges.)
We get user 2 via this command:
![image4](../../../../../_resources/image4-43.png)
We then can move into the root folder using user2:
![image5](../../../../../_resources/image5-32.png)
We then can access the ssh folder:
![image6](../../../../../_resources/image6-22.png)

Then we access there id_rsa and connect using ssh with there ssh key so we gain root access:
![image7](../../../../../_resources/image7-18.png)

We can copy this data and then place it into our local machine:
![image8](../../../../../_resources/image8-16.png)

We then can connect to root using
![image9](../../../../../_resources/image9-15.png)

And access the new flag
![image10](../../../../../_resources/image10-12.png)
