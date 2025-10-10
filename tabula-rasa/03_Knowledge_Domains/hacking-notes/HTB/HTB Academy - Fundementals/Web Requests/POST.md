---
title: POST
updated: 2023-01-21T20:43:52.0000000+00:00
created: 2023-01-21T20:17:38.0000000+00:00
date modified: Monday, May 13th 2024, 10:56:56 pm
---

Introduction:

Where GET places user parameters within the URL, POST places user parameters inside the HTTP Request body. The three main benefits of this are:

1.  ***Lack Of Logging:** a POST request can send large files, it is inefficient for the server to log all uploaded files as part of the requested URL.*
2.  ***Less Encoding Requirements:** URLs are designed to be shared, which means they can only be **alphanumerical**. But by transferring data inside the body, we can transfer different data types like binary.*
3.  ***More data can be sent:** Max URL length is limited, though it does vary between browsers (Chrome/IE/Firefox), web servers (IIS, Apache, nginx) and CDNs (Fastly, CloudFront, Cloudflare) and URL shorteners (bit.ly, azmn.to). URL lengths are usually below **2000** characters.*

Login Forms:

POST is frequently used in login forms and we can see that forms that use **PHP login form's** rather than **HTTP basic auth**:
![image1](../../../../_resources/image1-98.png)
*(Again we use admin:admin to log in.)*

If we clear our login attempts (using trash icon), then use the network tab (CTRL+SHIFT+E). We can see our POST request:
![image2](../../../../_resources/image2-79.png)
And we see our password and username in the **Request Payload.**

**We can copy this request to cURL** to see if we can log in using it as well. We need to use the **-X** flag to set our request method to post, then we can use:
![image3](../../../../_resources/image3-67.png)
*(Lots of login forms would redirect us to a login page, if we want to follow the redirection in cURL We can use the **-L** flag.)*
Authenticated Cookies:

If we get authenticated, we should receive a **browser cookie** that can **persist our authentication**. So that we don't need to constantly log-in.

We can the -v or -I flag, to check for the authenticated cookie, which should be under the **Set-Cookie** header:
![image4](../../../../_resources/image4-58.png)

We can then use this cookie in cURL using the **-b** flag, thus allowing us to login without needing to provide creds every time:
![image5](../../../../_resources/image5-44.png)
Alternatively, we can use:
![image6](../../../../_resources/image6-33.png)

With Dev-tools:

We can do the same thing using-dev tools, if we navigate to the **storage tab (SHIFT + F9).** We can look at cookies, using our earlier authenticated cookie we can replace the cookie value with our own, then refresh the page:
![image7](../../../../_resources/image7-27.png)
*(We then set the value to c1nsa6…., then refresh)*

This is an essential part of many web attacks like **Cross-Site Scripting.**

JSON data:

After we get to the City Search, we can go to the network tab in DevTools and make a request in JSON:
![image8](../../../../_resources/image8-23.png)
*(In this example, {"search":"London"})*

The POST data is in a JSON format, this means our request must have the **Content-type** header of **application/json**. We can confirm this by right-clicking on the request and selectin **Copy\>Copy Request Headers.** Note that to send a request we need the following details in our cURL line:

1.  *The PHPSESSID (using -b or -H)*
2.  *Content-Type: application/json (using -H)*
3.  *That we are using POST (using -X)*

Nintails@htb\[/htb\]\$ curl -X POST -d '{"search":"london"}' -b 'PHPSESSID=c1nsa6op7vtk7kdis7bcnbadf1' -H 'Content-Type: application/json'
\["London (UK)"\]

**Finally,** we can Copy \> Copy as fetch, then use the JS console to execute the same code.
