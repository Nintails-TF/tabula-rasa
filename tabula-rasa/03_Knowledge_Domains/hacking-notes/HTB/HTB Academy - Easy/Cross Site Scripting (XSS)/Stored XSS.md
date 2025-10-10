---
title: 'Stored XSS:'
updated: 2023-08-18T18:06:00.0000000+01:00
created: 2023-08-18T17:27:17.0000000+01:00
---

Introduction:

The most critical type of XSS vulnerability is **Stored/Persistent XSS**. Since if our injected XSS payload gets stored in the back-end database and retrieved upon visiting the page - **every user that visits the page can be afflicted.**

Since this vulnerability is very widespread and can effect lots of users and that it can be harder to remove the XXS payload from the back-end database - it is more critical for these reasons.

Stored XSS Example:

Taking a **To-Do list** for example, we can try add any text to the to-do list, *If there is no input sanitization or filtering applied to the user input **we may be able to exploit XSS.***

To **test XSS** we can use a basic payload:
![image1](../../../../_resources/image1-190.png)

If we see a popup after executing the JS code or after refreshing the page - **we know that XSS is possible**. Furthermore, we can confirm this by looking at our page source using **CTRL+U** to see our payload in the page source.

*Note that modern web apps use cross-domain Iframes for user input, so even if the web form is vulnerable to XSS, it would be not be a vulnerability on the **main web app.** This is why we want the **origin** so we can see what **URL** the XSS is being executed on.*

**If the payload is blocked**, since alert() functions can be blocked on modern browsers, we can use the **\<plaintext\>** payload which will stop rendering HTML code that comes after it. We can also use **\<script\>print()\</script\>** which will pop-up the browser print dialogue.

**To see if the XSS is persistent, we can refresh the page and check if we get the payload again.** This means that the payload is not unique to us.

Activity:
![image2](../../../../_resources/image2-156.png)

We can use an alert box to write details to the page, combining this with **document.cookie** we can see the current cookie on the document:
![image3](../../../../_resources/image3-121.png)

We can check if this is persistent, by refreshing the page, which will cause the same pop-up to appear again.
