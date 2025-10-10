---
title: 'Skills Assessment:'
updated: 2023-08-13T17:19:13.0000000+01:00
created: 2023-08-13T10:11:52.0000000+01:00
---

![image1](../../../../_resources/image1-180.png)

1.  Start up the ZAP fuzzer
2.  Add a cookie request to it
    1.  Add the part of the string we already know
3.  Fuzz the section at the end of the cookie using **alphanum-case.txt**
    1.  Encode the letter using base64 then using hex
    2.  ZAP enables you to encode using **base64** by default, **but not hex.**
        1.  What we can do instead is to encode the data via the console, then import the wordlist into ZAP
4.  **The encoded cookie is:** 4D325268597A6B7A596A686A5A4449314D4746684F474D7859544D325A6D5A6D597A6335595445335953413D
5.  Start fuzzing the login portal.

Using Burp Intruder:

We set our cookie using - to define our payload location:
![image2](../../../../_resources/image2-148.png)

We then go into our payload processing and import the wordlist then process it:
![image3](../../../../_resources/image3-114.png)

After some configuring around, we find a request that has a different length:
![image4](../../../../_resources/image4-91.png)

This request has our encoded admin cookie:
4d325268597a6b7a596a686a5a4449314d4746684f474d7859544d325a6d5a6d597a6335595445335957513d

And gives us the flag:
HTB{burp_1n7rud3r_n1nj4!}
I will be using ZAP here, since I can't afford Burp suite pro. I'll save the project under *HTB_webproxy_skillsAssessment*
![image5](../../../../_resources/image5-71.png)

1.  Make sure to go to IP:PORT/lucky.php
    1.  You don't need to add anything to hosts.
2.  We can go to the button code in the html, then remove the disabled attribute, we can then use the **break feature** in zap hud, in order to store the request, then we can add it to our sitemap:
    1.  ![image6](../../../../_resources/image6-48.png)
3.  We can then send requests over and over and get a flag response from the form:
    1.  ![image7](../../../../_resources/image7-42.png)
    2.  Note that these will be stored in our history.

![image8](../../../../_resources/image8-36.png)
1.  Navigate to the admin.php directory. We can look at the request in the HTTP header with the cookie:
    1.  ![image9](../../../../_resources/image9-30.png)
2.  Looking at our notes and the string, we see that this is **hex encoding.**
3.  After we decode the hex we get:
    1.  ![image10](../../../../_resources/image10-24.png)
    2.  Which we decode again since it is **base64** because of the = at the end.
4.  We decode this into our final string which is 31 characters long
    1.  ![image11](../../../../_resources/image11-18.png)
    2.  This is the admin cookie: 3dac93b8cd250aa8c1a36fffc79a17a

![image12](../../../../_resources/image12-13.png)

Metasploit Proxies:

We can search for the plugin we want to exploit, then route it through our web proxy like so:
![image13](../../../../_resources/image13-12.png)

