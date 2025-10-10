---
title: 'Intercepting Web Requests:'
updated: 2023-08-09T19:52:51.0000000+01:00
created: 2023-08-08T00:28:23.0000000+01:00
---

Introduction:

Now that we have set up our proxy, we are now able to intercept and manipulate HTTP requests. We'll start by learning how to intercept web requests, modifying them and sending them through their intended destination.

Burp:

The steps we need to follow in BURP is:

1.  Go to the intercept tab and **enable interception.**
2.  Once we enable interception traffic, we then need to forward each request, since all Firefox requests will be captured.

ZAP:

1.  We start our integrated browser and turn on request interception
    1.  ![image1](../../../../_resources/image1-168.png)
2.  We can navigate to break to forward the request.

We can also use the HUD:
1.  Open the hud
2.  Turn on break feature
    1.  **Step** - This will send a single request and examine its response
    2.  **Continue** - This will send all further requests.
    3.  **Drop** - This will drop the request.

Manipulating Intercepted Requests:

Once we intercept a request, it will hang until we either forward it or drop it. We can examine the request, figure out what it does and then manipulate it if necessary.

Web proxies help us exploit many vulnerabilities in this way, such as:

1.  SQL injections
2.  Command Injection
3.  Upload bypass
4.  Authentication Bypass
5.  XSS (Cross Site Scripting)
6.  XXE (XML External Entity)
7.  Error Handling
8.  Deserialization

