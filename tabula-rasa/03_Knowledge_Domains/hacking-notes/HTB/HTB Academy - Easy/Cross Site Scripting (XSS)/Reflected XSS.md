---
title: 'Reflected XSS:'
updated: 2023-08-18T18:45:27.0000000+01:00
created: 2023-08-18T18:06:16.0000000+01:00
---

Attack users with Reflected XSS:

Even though we know that a reflected XSS is present, the question still remains:

***How do we exploit this non-persistent vulnerability to target victims?***

This depends on which HTTP request is used to send input to the server - we can check this using **dev tools and the network tab.**

For instance, if a **GET request** is used, this means we can send parameters using the URL. So we can create a link that will perform our XSS payload when clicked on.
![image1](../../../../_resources/image1-191.png)

(Of course in a real attack, perhaps some kind of URL shortener would need to be used to avoid the user from catching on).

Introduction:

There are two types of **Non-persistent XSS,** those being **reflected XSS** (which is processed by the back-end server) and **DOM XSS** (which is fully client-sided). **Non-persistent XSS** is not stored through page refreshes - hence our attacks will only work on the targeted user rather than mass users.

**Reflected XSS** vulnerabilities occur when our input reaches the back-end and gets returned to us without being filtered or sanitized - there are many cases in which this can occur - like through error messages or confirmation messages.

In these cases, we can attempt using XSS payloads to see if they execute or not.

Reflected XSS example:

Again, using our to do list example, we first want to see what happens if we give the list a normal input:
![image2](../../../../_resources/image2-157.png)

Since we see an error message this means that the application could be vulnerable to **reflected XSS**. We can use the same payloads from **stored XSS** to check if it works:
![image3](../../../../_resources/image3-122.png)

We see that our payload isn't written to the page, but by looking at source code:
![image4](../../../../_resources/image4-97.png)

We can see that our script has been injected into the page.

