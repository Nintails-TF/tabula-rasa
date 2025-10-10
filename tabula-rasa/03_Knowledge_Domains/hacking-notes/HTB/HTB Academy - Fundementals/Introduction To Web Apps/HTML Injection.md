---
title: 'HTML Injection:'
updated: 2023-04-06T13:11:35.0000000+01:00
created: 2023-04-06T12:38:19.0000000+01:00
---

Introduction:

It is important to validate and sanitize input, some user input wouldn't make it to the back end. It is critical to validate and sanitize user input on the front end and back end.

**HTML Injection** occurs when unfiltered user input is displayed on the page. This can either be through retrieving previously submitted code. Or by displaying unfiltered user input through JavaScript on the front end.

When a user has complete control of how their input will be displayed. They can display HTML code display it as part of the page. This may include malicious HTML code, like a fake login form, to trick users into logging into to a malicious server to be collected.

**HTML Injection** can also be used for web page defacing. This consists of injection to new HTML code to change, inserting malicious ad, or even completely changing the page. This can result, in severe reputational damage to the company hosting the web application.

For Example:

If no input sanitation is in place, this is potentially an easy target for **HTML injection** and **Cross-site scripting (XSS).** We take a look at the page source code and check how the user input is displayed:
![image1](../../../../_resources/image1-106.png)
We can inject HTML into the front end using:
![image2](../../../../_resources/image2-86.png)

This will cause the **front-end** (only our browser) to display a background image within the body :
![image3](../../../../_resources/image3-72.png)
