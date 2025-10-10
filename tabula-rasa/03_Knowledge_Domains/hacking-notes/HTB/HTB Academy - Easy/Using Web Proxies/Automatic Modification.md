---
title: 'Automatic Modification:'
updated: 2023-08-10T09:56:46.0000000+01:00
created: 2023-08-10T09:16:07.0000000+01:00
---

Introduction:

There are also certain cases in which we will want to apply certain modifications to **ALL outgoing HTTP requests** or **ALL incoming HTTP responses**. In these cases, we need to use automatic modification. For example:

*Our current **user-agent** is blocked, so we need to change our **user-agent** to be different in all requests.*

BURP match and replace:

We can navigate toe **Proxy\>Options\>Match and replace** and we can add a new rule in BURP:
![image1](../../../../_resources/image1-171.png)

Where:
- Type: Request header
  - Tells burp we want to change details in the request header, not the main body of the request.
- Match: ^User-Agent.\*\$
  - This is the regex pattern to match the **whole line** with **User-Agent** in it.
- Replace:
  - This replaces the default user agent with our modified user-agent.
- Regex match: True
  - We don't know the exact line we want to replace, so we are going to regex any value that matches the pattern.

After this is done, we can verify this is working by visiting a page in the pre-configured browser:
![image2](../../../../_resources/image2-140.png)

Thus, we have our new user-agent.

Automatic HTTP Modification:

We can use a similar method of modification to change HTTP on the page. This time we can navigate to the **Response body** option. Since we want to change the body of the message, and we don't need regex since we know the exact string we want to replace:
![image3](../../../../_resources/image3-106.png)

This will make our changes persistent between page refreshes.
ZAP method:

ZAP has a similar method, called the **replacer** which we access using **CTRL + R** or by searching **Replacer** in the options menu, we then can add a new rule, we get a similar window:
![image4](../../../../_resources/image4-83.png)
Where:
- Description
  - A description of the rule
- URL
  - A regular expression to match the URL of the message ~~-~~ **empty rule applies to all messages.**
- Match Type
  - Tells ZAP where to change the details
- Match String
  - What string regex is looking for to replace
- Match regex
  - True
- Enable
  - Will activate the rule.

The ZAP rule **request header string, will work in the same way to the BURP method.**

ZAP also has another feature called **initiators**, which allows us to select where our rule will be applied, by default this is **All HTTP(S) messages** which applies it everywhere.

Searching google we can see:
![image5](../../../../_resources/image5-64.png)

ZAP persistent HTTP changes:
![image6](../../../../_resources/image6-43.png)
![image7](../../../../_resources/image7-37.png)

