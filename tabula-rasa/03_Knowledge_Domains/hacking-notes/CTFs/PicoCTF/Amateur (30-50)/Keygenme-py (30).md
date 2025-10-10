---
title: 'Keygenme-py (30):'
updated: 2022-08-31T18:57:59.0000000+01:00
created: 2022-04-10T16:09:47.0000000+01:00
---

![image1](../../../../_resources/image1-29.png)
We are given a program that is an *"Arcane Calculator"* about estimating mana burn. However; we aren't interested in that and what we want is the flag.

Initially, we see the partial flag as a variable in the calculator:

![image2](../../../../_resources/image2-27.png)

picoCTF{1n_7h3\_\|\<3y_of_xxxxxxxx}

Our goal is to get a complete license key so we can see the full decrypted program:

![image3](../../../../_resources/image3-23.png)

So we need to figure out the licence key from this code:

![image4](../../../../_resources/image4-17.png)
Firstly, we need to know what username_trial is:

![image5](../../../../_resources/image5-11.png)
Gives:  

![image6](../../../../_resources/image6-5.png)

Figuring out what hashlib.sha256() does and .hexdigest() does is key
In figuring out the correct license key.

<https://docs.python.org/3/library/hashlib.html>  

Using this we can print out the first if statement and compare it:

![image7](../../../../_resources/image7-4.png)

![image8](../../../../_resources/image8-3.png)

Oops, it looks like I've been inputting the license key wrong. I need to input the whole flag like so:

picoCTF{1n_7h3\_\|\<3y_of_ac73dc29}

All that was required was to print out each value of the hashlib hex digest then we make the index at the key equal that number.

I never even needed the key.

![image9](../../../../_resources/image9-2.png)

