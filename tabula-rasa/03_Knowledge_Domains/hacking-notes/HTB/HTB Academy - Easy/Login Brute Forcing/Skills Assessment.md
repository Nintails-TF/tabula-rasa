---
title: 'Skills Assessment:'
updated: 2023-08-17T14:34:58.0000000+01:00
created: 2023-08-17T13:15:06.0000000+01:00
---

Generating a personalised wordlist:

We now need to create a personalised wordlist for harry potter, so that we can log in using SSH.

1.  Go through cupp and input details about harry potter
    1.  We have harry.txt - 20k lines
2.  Remove passwords that cannot exist due to the policy
    1.  Must be greater than 8 characters
    2.  Must have a number
    3.  Must have a special character

![image1](../../../../_resources/image1-188.png)
(The issue with this word list is that it is too long! - going through cupp again and only putting in basic details - then adding details if you get no hits is better).

Now we need to make a username list:
![image2](../../../../_resources/image2-155.png)

Now we can launch our **hydra** brute force on the ssh login:
![image3](../../../../_resources/image3-120.png)

We have our creds for the SSH: **harry.potter:H4rry!!! -** Now we can log into the ssh server:
![image4](../../../../_resources/image4-96.png)

We can cat the flag:
![image5](../../../../_resources/image5-74.png)

![image6](../../../../_resources/image6-51.png)

We can see that g.potter is another user on the machine:
![image7](../../../../_resources/image7-44.png)

We can brute force her using the rockyou-30.txt that is on the server and via the open ftp port:
![image8](../../../../_resources/image8-38.png)
After about 5mins, we get the credentials:
![image9](../../../../_resources/image9-32.png)

We can switch user and just cat the flag:
![image10](../../../../_resources/image10-26.png)

![image11](../../../../_resources/image11-20.png)
When we try to access the website through a web browser, we are presented with **HTTP Basic Authentication:**
![image12](../../../../_resources/image12-15.png)

Since we have no credentials, we should start with brute-forcing default users:
![image13](../../../../_resources/image13-14.png)
We luckily get the credentials of **user:password** so that we can log into the webpage - we are presented with a second login and a flag:
![image14](../../../../_resources/image14-11.png)
HTB{4lw4y5_ch4n63_d3f4ul7_p455w0rd5}

![image15](../../../../_resources/image15-8.png)

We now need to login to the **admin_login.php** page, using burp we can look at the request/response data and pick a good success/failure flag:
![image16](../../../../_resources/image16-8.png)
We now have our PHP parameters: **user=admin&pass=admin**

We can set our flag as the login portion of the form - which will be unlikely to exist on the admin panel:
![image17](../../../../_resources/image17-7.png)

We now can use the flag: **\<form name='log-in'**

*(The reason we are using the **user** as the username, is because the hint in HTB academy suggests it).*

Now we need to construct our payload in hydra:
**hydra -l user -P** /usr/share/wordlists/rockyou.txt **-f** 83.136.252.24 **-s 45497 http-post-form "/admin_login.php:user=^USER^&pass=^PASS^:F=\<form name='log-in'"**
![image18](../../../../_resources/image18-7.png)
This gives us the creds to the admin portal - **user:harrypotter** - and now we have access to the admin portal:
![image19](../../../../_resources/image19-5.png)
