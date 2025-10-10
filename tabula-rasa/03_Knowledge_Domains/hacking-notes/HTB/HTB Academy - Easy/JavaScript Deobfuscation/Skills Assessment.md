---
title: 'Skills Assessment:'
updated: 2023-08-06T04:09:31.0000000+01:00
created: 2023-08-06T03:47:07.0000000+01:00
---

![image1](../../../../_resources/image1-166.png)
1.  By using CTRL+U to look at source code, we can see that the name of the script is **api.min.js**
    1.  ![image2](../../../../_resources/image2-136.png)

![image3](../../../../_resources/image3-104.png)
1.  We paste the JS into the Firefox console and get a flag looking output:
    1.  ![image4](../../../../_resources/image4-81.png)
    2.  HTB{j4v45cr1p7_3num3r4710n_15_k3y}

![image5](../../../../_resources/image5-62.png)
1.  We deobfuscate the code using [synchrony](https://deobfuscate.relative.im/)
2.  We then see that we can log the *return p* variable
    1.  ![image6](../../../../_resources/image6-41.png)
3.  We see a function named apiKeys()
    1.  ![image7](../../../../_resources/image7-35.png)

4.  This gives us the flag
    1.  HTB{n3v3r_run_0bfu5c473d_c0d3!}

![image8](../../../../_resources/image8-30.png)
Beautified code:
![image9](../../../../_resources/image9-26.png)

1.  We start a XMLHttpRequest
    1.  Which we know is used to send a web request
2.  The method used is POST, the URL we are sending data to is keys.php
3.  Currently, nothing is being sent.

We can send a custom POST request using cURL:
![image10](../../../../_resources/image10-21.png)
4150495f70336e5f37333537316e365f31355f66756e

![image11](../../../../_resources/image11-16.png)

We can decode the hex string, then we need to send another post request with our decoded key:
![image12](../../../../_resources/image12-11.png)

Sending our POST request:
![image13](../../../../_resources/image13-10.png)
HTB{r34dy_70_h4ck_my_w4y_1n_2\_HTB}
