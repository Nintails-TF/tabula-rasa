---
title: Proxy Setup
updated: 2023-08-08T00:28:12.0000000+01:00
created: 2023-08-07T23:20:31.0000000+01:00
date modified: Tuesday, May 14th 2024, 12:55:31 pm
---

Introduction:

Frequently, we need to use a real browser like Firefox. To use Firefox with a proxy we can manually go to Firefox preferences and set up the proxy using the web proxy. We can do this manually by configuring **port 8080,** but this is a pain in the ass.

**Foxy Proxy** is an extension that enables us to quickly change the Firefox proxy. We can download it here (<https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/>).
![image1](../../../../_resources/image1-167.png)

Once we are on the **options** page, we can add an IP and then we can use **127.0.0.1** on port **8080.** We then can call this proxy **BURP/ZAP.**

Installing CA Certificate:

Another important step when using a **web proxy** with our browser is to install the web proxy's CA Certificates. **If we don't do this HTTPS traffic may not get properly routed**.

We can install Both BURP and ZAPs certificate, by browsing to <http://burp> to get a CA certificate. For ZAP, we can navigate to **Tools\>Options\>Dynamic SSL Certificate**.

Installing Certificate:

Once we have our certificates, we can go to **about\>preferences and privacy.** Then we could **View Certificates.** We then need to go to the authorities tab and import our security certificate
![image2](../../../../_resources/image2-137.png)

