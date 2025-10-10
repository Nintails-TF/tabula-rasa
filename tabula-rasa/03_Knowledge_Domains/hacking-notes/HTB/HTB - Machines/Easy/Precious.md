---
title: Precious
updated: 2023-02-06T21:32:25.0000000+00:00
created: 2023-02-05T15:54:28.0000000+00:00
date modified: Monday, May 13th 2024, 10:16:13 pm
---

Enumeration:

Nmap scan:
![image1](../../../../_resources/image1-48.png)
![image2](../../../../_resources/image2-36.png)

We can't follow the redirect, so we should try adding it to our hosts file:
1.  Locate hosts file
    1.  Usually in /etc/
2.  Make sure to use sudo when trying to write to the host file, since it is read only otherwise.
![image3](../../../../_resources/image3-29.png)

This allows us to access the webpage:
![image4](../../../../_resources/image4-22.png)
It would be worthwhile to look at the request that occurs when a URL is fetched.

Looking a BURP request, we see that the data is sent in the URL field:
![image5](../../../../_resources/image5-14.png)

We can see that the server is running:
- **Nginx 1.18.0**
  - **Vulnerable:** <https://vuldb.com/?id.155282>
  - [CWE-444 (Request Smuggling)](https://cwe.mitre.org/data/definitions/444.html)
- **Phusion Passenger 6.0.15**
![image6](../../../../_resources/image6-8.png)
We learn this via Wappalyzer or by looking at requests. Seeing the Nginx can be exploited, we can try looking at Metasploit.

A little bit more enumeration:

Scanning using GoBuster - With the common wordlist we get nothing. So this looks to be a single page on HTTP.

We could also try:
- Dirsearch
- Wfuzz

But all don't return anything.

Metasploit:

Starting up Metasploit (msfconsole), we want to search for nginx exploits:
![image7](../../../../_resources/image7-6.png)
But nothing helps our case here.
HTTP Request Smuggling:

Since nginx is written in C, we can write a C reverse shell, then try to use CWE-444 to try and execute a reverse shell command by using a malformed HTTP request.

- Resources:
  - [Payload All The Things C Rev Shell](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#c)
  - [PortSwigger - Request Smuggling](https://portswigger.net/web-security/request-smuggling)

Converting to PDF:

We should first try and test the features for the website, i.e. we should convert a web page to a pdf. We can do this by:

1.  Starting a python http server
2.  Entering its port and IP address.

We can start a python http server, then use our tun0 Ip, so that we can download a pdf and test the website:
![image8](../../../../_resources/image8-4.png)
We get a PDF:
![image9](../../../../_resources/image9-4.png)
We can now inspect this PDF file - we do this by using **exiftool:**
![image10](../../../../_resources/image10-2.png)

We find out that it is made using pdfkit v0.8.6. And that it is vulnerable:
- <https://github.com/shamo0/PDFkit-CMD-Injection> \| This gives a POC on how the exploit works.
- <https://nvd.nist.gov/vuln/detail/CVE-2022-25765> \| CVE listing.

We can try the POC from Shamo0:

