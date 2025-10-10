---
title: 'Introduction:'
updated: 2023-08-18T17:26:53.0000000+01:00
created: 2023-08-17T15:15:12.0000000+01:00
---

What is XSS?:

XSS (Cross-site Scripting) is a very common vulnerability that is found in most web applications, XXS takes advantage of flaws in user input sanitization to **write** JavaScript code on to the page and to execute it client-side, this can lead to various different types of attacks.

Typically, we applications work by receiving the HTML code from the back-end server then rendering it on the client's browser. When a web application **doesn't sanitize user input** a malicious user can inject JS code into an input field - like the comment or reply feature.

**XSS vulnerabilities** are solely executed on the **client-side** and do not directly affect the **back-end server.** They only affect the user executing the vulnerability - this means that the direct impact of XSS vulnerabilities on the back-end are relatively low.

*However, XSS vulnerabilities are **very common** so they end up equating as being **medium risk** in web applications since (**low impact + high probability = medium risk).** We should always seek to reduce the occurrence of XSS, since they can lead to nasty **vulnerability chains**.*
![image1](../../../../_resources/image1-189.png)

XSS Attacks:

XSS vulnerabilities can facilitate a large range of attacks - a basic attack: **session hijacking** would involve having a target send their session cookie to an attackers web server - the attacker could then gain access to their account.

Another example is having the target's browser execute API calls that lead to malicious actions - like changing the **targets password, mining bitcoin and displaying ads.**

Since XSS attacks are executed within the JavaScript code inside the clients browser, they cannot execute code at a system wide level. **However,** XSS is frequently leveraged in more attacks like **heap overflows**.

Types of XSS:

There are three main types of XSS:

- **Stored XSS**
  - *This is the most critical type of XSS to patch - this occurs when user input is stored on the back-end database then is displayed upon retrieval.*
  - *This frequently occurs during posts or comments.*
- **Reflected XSS**
  - *Occurs when user input is displayed on the page after being processed by the back-end server.*
  - *This frequently occurs with search results or error messages*
- **DOM XSS**
  - *Same as reflected XSS - but this occurs when user input is shown directly in the browser and is fully-client sided - e.g. never reaches the back-end.*
  - *This frequently occurs during HTTP parameters and anchor tags.*

