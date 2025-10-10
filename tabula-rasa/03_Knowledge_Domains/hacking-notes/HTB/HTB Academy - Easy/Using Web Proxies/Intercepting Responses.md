---
title: 'Intercepting Responses:'
updated: 2023-08-10T09:15:54.0000000+01:00
created: 2023-08-09T20:09:05.0000000+01:00
---

ZAP Method:

With ZAP, we can use the ZAP hud and use break along with the **step** command to automatically intercept the response.

We can also use the lightbulb feature of **show/hide fields**, which enables us to quickly perform the same actions without needing to refresh the page.

The **comments** feature is also really good to check out too.
Introduction:

In some cases, we need to intercept HTTP responses from the server **before** they get to our browser. This is useful when we want to change how a webpage looks - like disabling certain fields or showing hidden fields.

BURP method:

We can enable this feature by navigating to **Proxy\>Options** and enabling **intercept response** under **intercept server responses.**
![image1](../../../../_resources/image1-170.png)

After we configure this interception, we can press **CTRL + SHIFT + R** to force our browser to perform a full refresh. Once we go back to burp we can see the intercepted server request and we can forward it:
![image2](../../../../_resources/image2-139.png)

We can change this request to enable us to have a max length greater than 3 and we can also change the type to text rather than number, enabling us to enter any value we want.

We then can go back to the browser and send any thing we want in the form, we can also use the same technique to access disabled buttons or hidden fields.
