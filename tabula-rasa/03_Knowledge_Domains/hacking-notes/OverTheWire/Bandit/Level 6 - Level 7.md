---
title: Level 6 -> Level 7
updated: 2022-07-21T18:28:02.0000000+01:00
created: 2022-07-21T18:02:55.0000000+01:00
---

We go to the root of the machine using:

![image1](../../../_resources/image1-217.png)

We then can execute our command to search the whole system for the file.

![image2](../../../_resources/image2-183.png)

We can the change our directory to that of the bandit7.password and then concatenate it.

![image3](../../../_resources/image3-145.png)![image4](../../../_resources/image4-118.png)

Looks like we need to find a file based on the follow details. Using man find we can find the following parameters.

![image5](../../../_resources/image5-89.png)

![image6](../../../_resources/image6-63.png)

And -size from Level 5 -\> Level 6

This command should work, but we don't know where the file is on the server, we need to figure out where files are located.

![image7](../../../_resources/image7-56.png)

