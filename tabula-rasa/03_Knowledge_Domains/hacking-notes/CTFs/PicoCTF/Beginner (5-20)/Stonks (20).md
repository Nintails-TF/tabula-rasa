---
title: Stonks (20)
updated: 2022-07-25T15:22:36.0000000+01:00
created: 2022-03-02T11:18:42.0000000+00:00
---

![image1](../../../../_resources/image1-24.png)
We can launch the C file in our own terminal like so:

![image2](../../../../_resources/image2-22.png)

However we do need to connect to the net or something for this to work.
From the hint that this is a binary exploitation activity, It sounds like I need to look at the source code and input a parameter that violates a boundary to help us get the API key.

Commonly it looks like memory vulnerabilities are the way. Within the buy_stonks method we can see a malloc of 300 + 1.

![image3](../../../../_resources/image3-18.png)

So if we can input data that is larger than 301 bytes then we can crash the program or do something?
![image4](../../../../_resources/image4-13.png)
The issue with the code that the program is vulnerable to: **Format String vulnerability**

This is when the submitted data of an input string is evaluated as a command by the application and is not sanitised. This allows code to be executed that will cause segmentation errors and overflow.

**The format function** - Is the printf which converts a variable to human language, we then can pass in a format string parameter that printf will take, like %x

<https://owasp.org/www-community/attacks/Format_string_attack> - is a good article on format string attacks.

![image5](../../../../_resources/image5-7.png)

What is big and little endian?:

Apparently this is in little endian:

b4654436f636970 345f7435306c5f49 306d5f796d5f6c6c 353861305f79336e

Meaning it needs to be converted into big endian so that the text can be read correctly.  

7069636F4354460B 495F6C3035745F34 6C6C5F6D795F6D30 6E33795F30613835

![image6](../../../../_resources/image6-3.png)

Ff99007d32356533, this is big endian, and converting it into little we get:

336535327D0099FF or the ending of the flag:

![image7](../../../../_resources/image7-2.png)

Our flag is picoCTF{I_L05t_4ll_my_m0n3y_0a853e52}
![image8](../../../../_resources/image8-1.png)![image9](../../../../_resources/image9-1.png)

What does this mean?

We can find the vulnerable line of code then pass arguments into it. This vunerable line of code is the printf string, since user input is not santiced you can input string format text to get hex back.

We can send %llx strings which stands for long long hex values that will end up printing the hex values from the stack.

This gives us the hex:

804b000098aa3d0\|f7ed8d80080489c3\|1ffffffff\|f7ee6110098a8160\|f7ed8dc7\|5098a9180\|98aa3d0098aa3b0\|7b4654436f636970\|345f7435306c5f49\|306d5f796d5f6c6c\|353861305f79336e\|ff99007d32356533\|f7ee6440f7f13af8\|1ebdcf600\|f7d75ce900000000\|f7ed85c0f7ee70c0\|ff9938a8f7ed8000\|f7ed85c0f7d6668d\|ff9938b408048eca\|f7efaf0900000000\|f7ed80000804b000\|ff9938e8f7ed8e20\|f7ed9890f7f00d50\|f7ed8000ebdcf600\|ff9938e80804b000\|98a816008048c86\|ff9938e8ff9938d4\|f7ed83fc08048be9\|ff99399c00000000\|1ff993994\|98a816000000001\|ff993900ebdcf600\|0\|f7ed8000f7d1bfa1\|f7ed8000\|1f7d1bfa1\|ff99399cff993994\|1ff993924\|f7ed800000000000\|f7f13000f7efb70a\|f7ed800000000000\|0\|e82db6c2792170d2\|0\|100000000\|8048630\|f7efb960f7f00d50\|10804b000\|8048630\|8048b8508048662\|ff99399400000001\|8048d3008048cd0\|ff99398cf7efb960\|1f7f13940\|

Now we need to look at the hex values that represent strings, we can either test all of these values by trying to convert them, or we can know the values of hex that represent text.

Converting hex to ascii in terminal:

![image10](../../../../_resources/image10-1.png)

We can pipe a file into here instead of using text

![image11](../../../../_resources/image11-1.png)

So we're getting there but we are missing out on something else key. It looks like need to understand what little and big endian is.

What are the text ranges of Hex?:

