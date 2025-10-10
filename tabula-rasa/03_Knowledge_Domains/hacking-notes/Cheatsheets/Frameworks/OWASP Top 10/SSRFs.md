---
title: SSRFs
updated: 2023-08-15T21:31:47.0000000+01:00
created: 2023-08-15T16:35:12.0000000+01:00
---

Types of SSRFs:

There are two types of SSRFs:

1.  **Regular / In band**
    1.  This means that you will request a page - let's say the admin page - in the response you will see the admin page.
2.  **Blind / Out of band**
    1.  This means if you request the admin page, but you don't actually see the admin page, In this example you would have to make a HTTP request on your server from the page to prove a Blind SSRF.

Impacts of SSRF Attacks:

This depends on the functionality of the application that is being exploited, but generally we need to consider:

- **Confidentiality -** Can be none/low/high
- **Integrity -** Can be none/low/high
- **Availability -** Can be none/low/high

In general, SSRFs can lead to sensitive data disclosure, scanning of internal networks, compromise of internal tools, even RCEs, etc.

Finding SSRFs:

**Blackbox Testing:**

- *Map the application*
  - *Identify any request parameters that contain hostnames, IP addresses or full URLs.*
  - *The most important step.*
- *For each request parameter, we can fuzz using **SSRF payloads** and see how the application responds.*
  - *If there is a defence in place - we can try circumvent it.*
- ***For testing blind SSRF -** modify a value on the server and send its value to a server you control and see if you get any requests.*
  - *If there aren't any requests, look at the time taken for the application to respond, if there is a long time to respond there may still be an SSRF.*

**Whitebox Testing:**

- Review the source code and identify all request parameters that accept URLs
  - Map the request parameters like a blackbox and search for them in the code.
- Determine the URL parser being used and try to circumvent blacklists and whitelists.

Exploiting SSRF vulnerabilities:

Introduction - OWASP definition:

A SSRF (**Server-side request forgery**) is when an attacker abuses a feature to read or update internal server resources.

An attacker can exploit an SSRF by supplying or modifying a URL which the webserver will read or submit data to. If this webserver doesn't validate user supplied URL.

SSRFs are dangerous, because they can lead to attackers being able to *Read server configurations, connect to internal services or perform POST requests towards internal services which are not intended for access.*

[Server-Side Request Forgery (SSRF) \| Complete Guide](https://www.youtube.com/watch?v=ih5R_c16bKc)

What is SSRF:

Taking the example, of an online shop in which a checkout feature is publicly facing:
![image1](../../../../_resources/image1-18.png)
When applications are designed in this format, there is a **trust relationship** between the **actors** that are connected to said web application - i.e. the cloud services and internal servers trust the requests from the web app.

For example, if a user wants to check how many cupcakes are in stock, they click on a button which sends a request to the server, the server processes this request and sends a response back on the level of stock:
![image2](../../../../_resources/image2-17.png)

After a user checks the stock, they will then want to buy an item, this will send a request to the 3rd party system to process the purchase request:
![image3](../../../../_resources/image3-13.png)

**The danger occurs if these URLs/requests are not properly validated by the backend**. Then there is potential for the user to modify the requests by tampering with the URL:
![image4](../../../../_resources/image4-9.png)

In summary, if we were to send a request to delete, add or view certain items, we would get denied by the firewall, but if we got access to the admin panel, we could see the **trusted URL** by looking at source code or request data, and then go on to adding, deleting or viewing items.

Beyond this, you could use the SSRF to use the afflicted web application as a **proxy** and enabling you to **run automated scans through the website to look for more vulnerabilities on the internal network.**

**We can also use SSRFs to exploit the cloud:**
![image5](../../../../_resources/image5-5.png)

This is exactly what happened in the **Capital One** data breach, in which the attacker gained access to s3 buckets and gained access to **100 million credits cards and accounts.**

