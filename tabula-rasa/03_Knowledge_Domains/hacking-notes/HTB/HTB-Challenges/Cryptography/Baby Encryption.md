---
title: 'Baby Encryption:'
updated: 2023-08-14T17:04:36.0000000+01:00
created: 2023-08-14T14:45:41.0000000+01:00
---

Introduction:

We download the zip file and get two files:
1.  Chall.py
    1.  This appears to be the script that wrote the encrypted message
2.  Msg.enc
    1.  This appears to be a hex encoded message.

It seems like we will have to work our way through the program code and figure out how our message was encoded.

Chall.py:
![image1](../../../../_resources/image1-206.png)

Main program flow:
1.  Encrypt a message (MSG) which has been created using the **secret** library.
    1.  The return statement returns ct in bytes?
2.  Create a new file, msg.enc in write mode
3.  Write the message to file, encrypted in hex.
4.  Close the file.

Why does the brute force method work?

Decrypting msg.enc:

First let's remove the **hex** encoding, we can use **xxd** for this purpose:
![image2](../../../../_resources/image2-172.png)

Then writing it to a file:
![image3](../../../../_resources/image3-137.png)

*We could probably reverse engineer the code and write a python script that would reverse the encoding done by the program.*

Reversing the code:

1.  Read the ciphertext into the program
2.  Reverse the operations performed on each character
    1.  **We cannot reverse modulo.**
3.  Write the output to file.

Our program to reverse encryption:
![image4](../../../../_resources/image4-112.png)

![image5](../../../../_resources/image5-86.png)
