---
title: Intro to web proxies
updated: 2023-08-07T23:06:00.0000000+01:00
created: 2023-08-06T19:55:28.0000000+01:00
date modified: Monday, May 13th 2024, 10:47:33 pm
---

Burp Suite:

**Burp suite** is the most common web proxy, as it has a easy to read user interface and various features like an in-built Chromium browser. Certain features are limited in the free version such as:

1.  Active web app scanner
2.  Fast Burp Intruder
3.  Loading Burp Extensions

The free version is usually enough for most tasks, however for more advanced applications of pen testing, the **pro version** can be handy.

OWASP ZAP:

The **Zed Attack Proxy** (ZAP) is another common web proxy tools for web testing, it is **free and open source** created and maintained by the **OWASP** community.

ZAP has a few advantages over BURP - mainly being free and open-source and gaining many features of **burp pro.**

Both tools are valuable, but if we cannot justify the licence fee of **burp pro**, we can use ZAP. However for more advanced pen tests or corporate tests, we can find usage withing Burp pro.
Introduction:

Most modern web and mobile applications work via sending requests to data to the back-end and receiving data from them and finally processing the data on the client side.

Because of this convention, it is **very important** that we secure our **back-end servers.**

The bulk of testing web applications involves **sending web requests** to the backend, so **web proxies** have been made to speed up the process of testing.

What are web proxies?:

Web proxies are tools that are set up *between* web browsers and the back-end server. We use them to capture and view all the web requests being sent by both the client and the back-end. *Inherently, web proxies are MITM (Man-in-the-middle) tools.*

You have other tools like **Wireshark** which analyse **all local traffic** to see what is passing through. But web proxies mainly work with **HTTP/80** and **HTTPS/443.**

**Web proxies are almost an essential tool for any pen tester**. The need to simply the process of capturing and replaying web requests via a program rather than earlier CLI-tools is very strong. Furthermore, the ability to intercept and modify requests is also really important.

Uses of web proxies:

Whilst the primary purpose of using web proxies is to **capture and replay HTTP requests**, other features of popular web proxies are:

- Web app vulnerability scanning
- Web fuzzing
- Web crawling
- Web application mapping
- Web request analysis
- Web configuration testing
- Code reviews

The most common proxy tools are **Burp Suite** and **ZAP.**
