---
title: Matryoshka Doll (30)
updated: 2022-08-31T18:58:01.0000000+01:00
created: 2022-04-10T15:18:43.0000000+01:00
date modified: Friday, May 17th 2024, 5:09:06 pm
---

![image1](../../../../_resources/image1-30.png)
We get an image file of some Russian doll. The image doesn't say anything, but if we can look at the metadata of the image, it might contain something. Look like using a command line tool named *imagemagick* can help us with this.

![image2](../../../../_resources/image2-28.png)

Using both binwalk and xxd to look at the file in a hex editor we see a file
Named base_images/2_c.jpg (it looks like a zip file):

![image3](../../../../_resources/image3-24.png)

The question is how do we access this file? We can do this by using binwalk -e:
![image4](../../../../_resources/image4-18.png)

This gives us another zip and the base-images folder which has the russian
Doll image:
![image5](../../../../_resources/image5-12.png)
Opening up the second file gives us, another Russian doll and give us the
Image 3_C.
After repeating this for a few steps and the resolution of the image
Decreasing every time, we get to a txt file that has the flag.

![image6](../../../../_resources/image6-6.png)

Interestingly, we see that dolls.jpg is actually in a png format? What if we try open the image as a png?

Using mv we can rename (move) files.
![image7](../../../../_resources/image7-5.png)

Sadly, this doesn't reveal anything:
![image8](../../../../_resources/image8.jpeg)

Looking at a CTF guide (<https://ctfs.github.io/resources/topics/steganography/file-in-image/README.html>)

We can see that another good idea is to open the file in a hex editor and use binwalk.
![image9](../../../../_resources/image9-3.png)
