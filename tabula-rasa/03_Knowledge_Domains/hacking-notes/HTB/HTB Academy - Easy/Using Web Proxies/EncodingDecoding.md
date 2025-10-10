---
title: 'Encoding/Decoding:'
updated: 2023-08-11T10:22:45.0000000+01:00
created: 2023-08-10T12:14:39.0000000+01:00
---

Introduction:

When we send and modify HTTP requests, we may need to perform encoding/decoding in order to interact with the webserver properly, as there can be filtering tools in place to prevent our requests. We can use the built-in encoders within web proxies to help us with this.

URL Encoding:

It is important when we are sending data in the URL that we set our **request headers** correctly. Otherwise we get errors in our responses, so we need to make sure to encode our characters correctly, mainly:

- Spaces
  - These can indicate the end of a request if not encoded.
- &
  - Otherwise interpreted as a parameter delimiter
- \#
  - Otherwise interpreted as a fragment identifier.

**On Burp suite**, we can right-click on requests and then convert them **into URL Encode key characters** or by selecting text and **pressing CTRL+U**.

**On ZAP**, all URL encoding is done automatically.

Consequently, we may also need to use **Full URL-Encoding** or **Unicode URL Encoding.** Which is helpful for requests that have lots of special characters.

Decoding:

Frequently, we will encounter web apps that encode their data into a particular format, so we may need to decode this to figure out the original statement. Also, **back-end servers** may expect data that is encoded in a certain format so way may need to encode our request data before we send it.

The following encoders are support by both Burp and ZAP:

- HTML
- Unicode
- Base64
- ASCII hex

**In Burp,** we can go to the decoder tab.
**In ZAP,** we can go to the **Encoder/Decoder/Hash** option or press **CTRL+E.**

For example, say we have a cookie that is base64 encoded: **eyJ1c2VybmFtZSI6Imd1ZXN0IiwgImlzX2FkbWluIjpmYWxzZX0=**

Using CTRL+E in ZAP:
![image1](../../../../_resources/image1-173.png)

*Whilst in ZAP we can create customized tabs and we can **add new types of encoders/decoders.***
Encoding:

As we can see from our decoded cookie:

*{"username":"guest", "is_admin":false}*

If we wanted to try get admin using the cookie, we could try to modify the cookie to:

*{"username":"admin", "is_admin":true}*

This would check to see if the cookie can change our level of privilege, then we would need to encode the cookie again back into base64:
![image2](../../../../_resources/image2-142.png)

Finally, we can send a request with the new cookie. Note that URL encoding looks similar to:
![image3](../../../../_resources/image3-108.png)

With URL decoding:
![image4](../../../../_resources/image4-85.png)

