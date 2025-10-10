---
title: 'Introduction:'
updated: 2023-02-03T16:56:08.0000000+00:00
created: 2023-01-22T17:46:31.0000000+00:00
---

Security Risks of Web Applications:

Web applications are a prevalent target for exploitation, no matter how big or small they are. Since anyone with a PC and an internet connection can exploit a web application.

There are also many automated scanning and attacking tools that target web apps, that allow for miscreants to damage a web application or company. Furthermore, as web apps become more complicated and advanced, the odds of critical vulnerabilities developing only increases.

A successful attack can lead to large business loses and business interruptions. User or corporate data can be leaked, so making sure that applications are thoroughly tested is key.

A common model for testing web applications is the **OWSAP Web Security Testing guide (**<https://github.com/OWASP/wstg/tree/master/document/4-Web_Application_Security_Testing>)

**Starting an attack**, commonly begins with reviewing the front and backend components of the application (i.e. Looking at HTML, CSS, JavaScript), then attempting to find vulnerabilities such as **Sensitive Data Exposure** and/or **Cross-Site Scripting (XSS).**

Once the front end is tested thoroughly, we move on to looking at the interaction between the browser and the backend webserver and **enumerate the technologies** that the web server uses to look for exploits.

We should also consider attacks from an Authenticated (signed in as a user) and **Unauthenticated** point of view.

Attacking Web Applications:

Pretty much every company has an outwards facing web application(s). From blogs, to login pages to online shopping portals. You are unlikely to find any serious vulnerabilities at a first glance. But there is a chance since web applications are so wide.

**It is not uncommon**, to chain vulnerabilities to get RCE. The **SQL-Injection** is a well-known vulneability that still is prevalent today, can allow the access of sensitive data. This usually occurs because of web applications that rely on **Active Directory**. As it has exploits that allow us to get **emails** of admins/users.

This allows us to perform **password spraying** on various web portals. (This is the act of testing a single password against many different accounts, to avoid getting locked out).

A pen tester that has a strong foundation in web applications can find many flaws that other miss. A few more examples of web application attacks are:
![image1](../../../../_resources/image1-102.png)
All of these examples can be found in the [OWASP cheat sheet.](https://cheatsheetseries.owasp.org/index.html)

Introduction:

Web applications are interactive applications that run on web browsers. Web apps often use a **client-server architecture** to handle interactions. There is a front-end component (What the user/client sees) and a back-end component (What the server/databases sees).

These web apps are used to make powerful tools like **Gmail, Amazon and Google Docs**. These Web apps are not exclusive to big corporations, but there are millions of web apps made by developers.

Web Applications VS Websites:

In general, the biggest different between **Web Applications** and **Websites** is there level of interactivity. *Websites are more static and don't contain as many functions.* Whilst **web applications** are more dynamic in nature:
![image2](../../../../_resources/image2-83.png)

Web applications can be refers to **Web 2.0**, whilst static webpages could be referred to **Web 1.0**. Other differences include:

- *Being modular*
- *Running on any display size*
- *Running on any platform without being optimized.*

Web Applications VS Native Operating System Applications:

**Web applications**, unlike native applications, are platform independent and don't require any space on the user's hard drive and functionality is achieved via executing commands remotely on the server.

Another advantage of web applications is there **Unity**. How every user gets the same version of the website that is being ran on the server. This makes patching easier and reduces maintenance and support costs.

Native apps do have an advantage in speed and their ability to use system libraries and local hardware. They are much faster and have a deeper integration with the OS. There are also hybrid web apps that use modern frameworks to try and get the best of both worlds.

Web Application Distribution:

There are many open-source web applications that are used by organisations and companies worldwide, that can be customized and edited, The most common are:
- WordPress
- OpenCart
- Joomla

Furthermore, you have closed source web apps, in which are sold by a company then bought by other users via a subscription fee, these include:
- Wix
- Shopify
- DotNetNuke

