---
title: 'HTTPS Requests:'
updated: 2023-01-20T08:18:58.0000000+00:00
created: 2023-01-19T13:31:01.0000000+00:00
---

Introduction:

HTTP has a fatal flaw, since all data is transferred in clear text, meaning that if hacker performs a MiTM (Man-in-the-middle) attack, that they can view potentially sensitive user data. To counter this, the HTTPS (HTTP secure) protocol was made.

HTTPS is now the mainstream way of requesting information over the internet, it means that even if there is a man in the middle, the data he sees is encrypted. For this reason, HTTP is being phased out and replaced with HTTPS.

Comparison:

HTTP request:
![image1](../../../../_resources/image1-92.png)

We can see that since the data is sent in clear text, an attacker on the same network, can grab user credentials from forms, then can use them for malicious purposes.

HTTPS request:
![image2](../../../../_resources/image2-73.png)

The data is transferred in a single stream of encryption, which makes it difficult to get meaningful information like credentials.

*Note that all data that is transferred via a HTTPS is encrypted. The request will still reveal the visited URL, if contacting a clear-text DNS server. This is why it is recommended to use an encrypted DNS server (8.8.8.8, 1.2.3.4) or use a VPN to ensure that all traffic is encrypted properly.*

cURL for HTTPS:

cURL should handle all HTTPS requests and perform secure handshakes and encrypt and decrypt data automatically. *However, if we ever contact a website with an **invalid SSL certificate** or an **outdate one**.* Then cURL, will not proceed with the communication to protect against MITM attacks.

This can be an issue when testing local web apps or a web app that is hosted for practical purposes, as such web apps that don't have a valid SSL certificate. *We can skip the certificate check with the flag **-k.***

Invalid SSL certificate:
![image3](../../../../_resources/image3-62.png)

Going through with the request anyways:
![image4](../../../../_resources/image4-53.png)

HTTPS Flow:
![image5](../../../../_resources/image5-41.png)

We can summarize this abstraction as:
- The user tries to perform a HTTP request
  - This request is redirected to the HTTPS website
- A HTTPS connection is initiated.
  - The client and server send hello packets of data giving info to each other.
  - The key exchange begins
  - Then an encrypted **handshake** is performed to make sure that encryption and transfer are working correctly.
- Once these are done, normal HTTP communication occurs.

Bonus - HTTP Downgrading:

An attacker can perform a HTTP downgrade attack, in which a Man-in-the-middle proxy is setup, which redirects the hosts traffic to the attackers host without user knowledge, allowing an attacker to see plain HTTP.

Most modern browsers, servers and web apps prevent this type of attack however.
