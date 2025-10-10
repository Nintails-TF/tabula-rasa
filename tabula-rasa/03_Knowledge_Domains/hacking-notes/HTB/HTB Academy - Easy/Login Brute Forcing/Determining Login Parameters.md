---
title: 'Determining Login Parameters:'
updated: 2023-08-16T14:10:16.0000000+01:00
created: 2023-08-16T13:56:56.0000000+01:00
---

Using Browser:

We can look at form parameters using **developer tools** that are built-into the web browser. In this case we will want to look at the **network tools** by pressing **CTRL+SHIFT+E.**

We can then try to log in using any credentials to run the form, the network tools will then show the event and reveal the request we want send or use in our brute forcing operation:
![image1](../../../../_resources/image1-184.png)

We can copy the raw POST parameters which will give us:
![image2](../../../../_resources/image2-151.png)

Another option would be to **Copy \> Copy as cURL** which would copy the whole cURL command so we could repeat the HTTP request in our terminal - **this would also give us our POST parameters:**
![image3](../../../../_resources/image3-117.png)

Using Web Proxies:

Similarly to dev tools we can also use web proxies like burp to send a request and look at the parameters:
![image4](../../../../_resources/image4-93.png)

This again gives us the PHP POST parameters.
