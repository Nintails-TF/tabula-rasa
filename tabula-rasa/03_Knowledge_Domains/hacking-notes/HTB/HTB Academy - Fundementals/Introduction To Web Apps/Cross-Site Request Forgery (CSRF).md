---
title: 'Cross-Site Request Forgery (CSRF):'
updated: 2023-07-17T10:27:39.0000000+01:00
created: 2023-07-16T10:03:20.0000000+01:00
---

Introduction:

The third main type of front end vulnerabilities is caused by **unfiltered user input** is called **Cross-Site Request Forgery** (CSRF). CSRF attacks may use XSS vulnerabilities to perform queries and use API calls on a web app that the victim is currently authenticated to.

This enables the attacker to perform actions as the authenticated user, CSRF also can use other vulnerabilities to perform the same function, like using HTTP parameters for attacks.

Common CSRF Ideas:

A common CSTF attack is an attack that is used to try and gain higher privilege access via a JS payload that automatically changes the victims password to whatever the attacker wants. Once the Victim vies the payload on the vulnerable page (e.g. a malicious comment that has the JS CSRF payload).

*The JS would **automatically execute** and use the victim's logged-in session to change their password, then the attacker can sweep in and compromise the account.*

Another common attacking idea with CSRF, is to target **admin accounts** or employee accounts. Since they usually have more sensitive functions which can be a potential vector to take control of parts of the back end. So instead of returning a session cookie we could inject a JS file:

**"\>\<script src=//www.example.com/exploit.js\>\</script\>**

Complexities:

However actually developing an exploit in JavaScript to change passwords requires understanding of the web app's password changing procedure and API usage. So creating a JS payload to give you this functionality is not easy.

Adage:

Honestly, it seems like either rushed/incompetent developers are generally the route of most security holes in especially CSRFs, but in security as a whole - as long as companies continue to give strict deadlines and mistakes are made by developers - more and more automated systems are going to be put in place that will by eventually bypassed.
Prevention:

***There should always be consideration from developers to filter/sanitize user input on the front end.***

e.g. we need to apply these two techniques:

1.  **Sanitization** involves stripping special characters and non-standard characters before storing them.
2.  **Validation** involves parsing user input and ensuring that the input matches the expected format.
    1.  So making sure an @ symbol is in an email field for a form.

We also need to sanitize what we display to users, in the event that an attacker manages to bypass the front and back end filters, so that no sensitive info is displayed on the front end.

Solutions:

Once we have sanitized/validated user input and displayed output, we can prevent **HTML injection, XSS, CSRFs.** Another method of preventing these attacks is to use a WAF (web application firewall).

A WAF helps prevent injection attempts automatically via inspecting HTTP traffic and blocking traffic it deems malicious. WAFs are normally used to prevent credit card fraud.

WAFs are not perfect and can still be bypassed - so developers should follow best practices and not over rely on web application firewalls.

Finally, modern browsers have built in anti-CSRF measures, which prevent automatic execution of JavaScript - of which are implemented using http headers and flags that stop automated requests.

(**Anti-CSRF** tokens or **http-only/X-XSS-Protection**, etc.)

However, all of these methods can still be bypassed and CSRFs still pose a large security vulnerability.

[CSRF cheatsheet OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
