---
title: Reverse/Baby Reverse
updated: 2022-10-22T23:30:18.0000000+01:00
created: 2022-10-21T23:22:12.0000000+01:00
---

![image1](../../../../_resources/image1-41.png)
We are given an ELF executable, when we run this we get:
![image2](../../../../_resources/image2-32.png)

Looking at the question, we might have to reverse the file in some way?

<https://0x00sec.org/t/dissecting-and-exploiting-elf-files/7267>

Looks like we should get the file information and start dissecting it base on this guide.

Getting the file type:
![image3](../../../../_resources/image3-26.png)

Using hexdump reveals the flag:
![image4](../../../../_resources/image4-20.png)
cvctf{r3v3r53_15_4w350m3}
