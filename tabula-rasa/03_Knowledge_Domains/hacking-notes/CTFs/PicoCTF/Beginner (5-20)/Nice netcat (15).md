---
title: 'Nice netcat (15):'
updated: 2022-03-02T11:05:00.0000000+00:00
created: 2022-03-02T10:59:55.0000000+00:00
---

Nice netcat (15):
![image1](../../../../_resources/image1-22.png)
02 March 2022
10:59

![image2](../../../../_resources/image2-20.png)

First things first, run the command in terminal:

![image3](../../../../_resources/image3-16.png)

We are returned numbers from the web request. I assume that it could be ASCII or something?

Pasting the numbers into a text file and then using a binary to ascii converters gives us:

![image4](../../../../_resources/image4-12.png)
I guess my hunch was right.
We know that NC allows us to connect to a host and get information from it.
