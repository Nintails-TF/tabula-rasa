---
title: 'HTTP Requests:'
updated: 2023-01-19T13:22:21.0000000+00:00
created: 2023-01-19T08:10:40.0000000+00:00
---

Introduction:

The **hypertext transfer protocol (HTTP),** is the main method of web and mobile applications to communicate with computers. HTTP is an application-level protocol and is used to access resources on the Worlds Wide Web.

**Hypertext** refers to text containing links to other resources that readers can interpret.

HTTP communication consists of a client and a server, in which the following process occurs:

1.  The client requests the server for a resource
2.  The server processes the request and the server returns the requested resource.
    1.  Note that the default HTTP port is port 80. It can be changed to other ports depending on the web server configuration.

The same requests are utilized when we visit different websites. So when we enter a ***Fully Qualified Domain Name (FQDN)** as a **Uniform Resource Locator (URL)**.* To reach the websites we want to get to, like [www.google.com](http://www.google.com) and [www.hackthebox.com](http://www.hackthebox.com)

URL:

Resources over HTTP are accessed via a **URL**. Which offers lots of specifications and customization of which resource we want to access:

![image1](../../../../_resources/image1-91.png)

The mandatory fields are:
- **Scheme**
- **Host**

/etc/hosts:

Our browsers look up records in our local /etc/hosts file and if the domain doesn't exist, then it would ask the DNS server for the record.

We can do manual DNS resolution by adding and IP + Domain name combo to access websites too. This can be useful when attacking machines/boxes.

cURL:

**cURL** (Client URL) is a command line tool that we can use along with HTTP (and lots of other protocols too) to send web requests via the command line.

This makes it good for sending ***automated web requests*** and making it ***essential*** for many different types of web pen testing. To send a basic HTTP request we can use cURL like so:
![image2](../../../../_resources/image2-72.png)

This will print the raw HTML (No JS/CSS) and allows us to inspect the page quickly.

**Downloading a html file -** We can also use cURL to download HTML pages, like so:
![image3](../../../../_resources/image3-61.png)
***(You can also use the -s flag to hide other statuses)***

Finally, you can use various commands to get help:
- Curl -h
- Curl --help all
- Curl --help category \[--help http\]
- Man curl

URL Component Cheat Sheet:

![image4](../../../../_resources/image4-52.png)

The Flow of a HTTP request:
![image5](../../../../_resources/image5-40.png)

This is a very abstract version of a HTTP request, the following steps are performed:

1.  *The user requests to go to the URL (**inlanefreight.com)***
2.  *The DNS (Domain Name Resolution) server, returns the IP in which the requested resource is at.*
    1.  *This DNS request is sent back to the clients browser*
3.  *A **GET** request is sent from the users browser to the web server on port **80**.*
    1.  *By default we should get sent to the **index.html** page of **inlanefreight.com**.*
4.  *The web server returns a HTTP response (200 - meaning that the request went through just fine).*
5.  *The web browser loads the page.*

Questions:
![image6](../../../../_resources/image6-30.png)

Answer:
![image7](../../../../_resources/image7-24.png)
