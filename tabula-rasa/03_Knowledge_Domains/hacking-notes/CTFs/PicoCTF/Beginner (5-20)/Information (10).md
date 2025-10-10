---
title: 'Information (10):'
updated: 2022-03-06T17:43:49.0000000+00:00
created: 2022-03-02T10:40:58.0000000+00:00
---

Using Exif tool you can get:

![image1](../../../../_resources/image1-20.png)

Then by decoding the license from base 64 you get the flag:

picoCTF{the_m3tadata_1s_modified}
We are given an image of a cat and asked to find the flag, The problem statement hints at changing files in a secret way.

Using ls -l we get the following:

![image2](../../../../_resources/image2-18.png)

I figured out that you can use stat instead to make the information more human readable:

![image3](../../../../_resources/image3-14.png)

Using file, you can determine what the file actually is, which in this case is a jpeg:

![image4](../../../../_resources/image4-10.png)

