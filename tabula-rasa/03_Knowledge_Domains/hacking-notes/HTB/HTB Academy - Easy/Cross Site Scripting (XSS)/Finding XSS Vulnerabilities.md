---
title: Finding XSS Vulnerabilities
updated: 2023-08-20T14:38:12.0000000+01:00
created: 2023-08-18T20:25:46.0000000+01:00
date modified: Monday, May 13th 2024, 11:09:44 pm
---

Introduction:

Now that we have a good idea about what XSS vulnerabilities are we need to figure out how to find them. In **web app pentesting finding vulnerabilities is as difficult as exploiting them**. However we have tools that can help us find XSS vulnerabilities.

**Web Proxies** like ZAP, Burp and Nessus all are able to scan and detect XSS vulnerabilities via both their active and passive scans. Paid tools usually will see you having more success, we can still use various open source tools to look for potential XSS vulnerabilities.

Automated Discovery:

Common tools we can use to discovery XSS vulnerabilities are **XSS Strike, Brute XSS and XSSer.** We can install **XSS Strike** using:
![image1](../../../../_resources/image1-193.png)

We can then provide XSS strike with a URL and search for XSS vulnerabilities:
![image2](../../../../_resources/image2-159.png)

Manual Discovery:

When it comes to manual XSS discovery the difficulty in finding various XSS vulnerabilities depends on the level of security of the web application, we can find basic XSS vulnerabilities via XSS payloads but finding more advanced XSS requires advanced understanding of code.

**XSS payloads** are the most basic method of testing for XSS vulnerabilities - we have huge payload lists like [**PayloadAllTheThings**](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/README.md) and **PayloadBox** - in which we can paste each of these payloads into input boxes to check if they are vulnerable or we can make a script to automate this.

*Note that XSS can be injected into any input in the HTML page - this includes: **HTTP headers, Cookie fields or user-agents.***

Most payloads don’t work with our example - even though we have the most basic form and example in place. This is because payloads are frequently written for a wide variety of **injection points** or are designed to bypass security features like **input sanitization.**

Our payloads can be written in \<script\> tags or other HTML attributes like the \<img\> tag and CSS style attribute too.

**The best method for manually testing for XSS is to write a python script and customize it for the website that is at hand.**

Code Review:

By looking at code and figuring out what it does we can more accurately discover XSS vulnerabilities. This way we can construct our own payload that will work accurately.

*Note that we should consider both the front and back-end code which is interacting with our input.*

**Running automated scanners and using XSS payloads is unlikely to give us many vulnerabilities** - this is because developers can run the same tools and patch them before code becomes live.

Activity:

Using XSStrike we can find that the email field is vulnerable to cross-site scripting:
![image3](../../../../_resources/image3-124.png)
The email filter doesn't like brackets and braces.

Even though, the email filter states that the input is invalid we can still send it to the server - using the payload: **\<svg onload=alert(1)//** , we get:
![image4](../../../../_resources/image4-99.png)

Refreshing the page results in the same alert - meaning that this is **stored XSS or reflected.** After we hard refresh the page, we see that the alert no longer is occurring.

