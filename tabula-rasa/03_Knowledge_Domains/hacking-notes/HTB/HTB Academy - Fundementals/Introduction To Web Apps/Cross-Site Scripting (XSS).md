---
title: Cross-Site Scripting (XSS)
updated: 2023-07-16T09:50:00.0000000+01:00
created: 2023-07-16T09:32:17.0000000+01:00
date modified: Tuesday, May 14th 2024, 12:01:44 pm
---

Introduction:

HTML injections are often used to perform **cross site scripting** attacks via injecting JavaScript code. *Once we execute the JS on the victim's machine, we can potentially gain access to the victim's account or even their device.*

**XSS** is similar to the HTML injection in theory. However, XSS attacks use JavaScript to perform more advanced attacks, rather than just defacing a website using HTML. *If HTML injection is a pistol, then XSS is a bazooka.*

Types of XSS:

There are 3 main types of XSS attacks:

1.  **Reflected XSS**
    1.  *This is when user input is displayed to the webpage after processing - so via insecure searching features, error messages, buttons and widgets, etc.*
2.  **Stored XSS**
    1.  *This is when user input is stored in the back end, usually in some kind of database that we can then retrieve data from. Think posts, comments, descriptions, etc.*
3.  **DOM XSS**
    1.  *This is when user input is written to the DOM (Document Object Model) - so think about the writing to the \<body\> tag, page title, etc.*

With our HTML injection - we had no ***input sanitisation** -* so we can also perform an XSS attack to show the cookie value of the current user:

JS:
**\#"\>\<img src=/ onerror=alert(document.cookie)\>**

Output:
![image1](../../../../_resources/image1-107.png)

We can see that the XSS payload is modifying the HTML DOM to give the current users cookie in a pop-up. We can leverage this to **steal cookie sessions** and **authenticate to the victims account**.
