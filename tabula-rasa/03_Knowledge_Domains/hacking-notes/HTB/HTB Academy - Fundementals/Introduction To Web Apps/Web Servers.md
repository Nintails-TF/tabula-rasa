---
title: 'Web Servers:'
updated: 2023-07-18T16:51:00.0000000+01:00
created: 2023-07-17T10:47:03.0000000+01:00
---

![image1](../../../../_resources/image1-110.png)
Introduction:

A web server is an application that runs on the back-end, it handles all of the HTTP requests from clients. It routes the client to the requested pages and sends a response. Web server usually run on **port 80** or **port 443**. Web servers also are responsible for connecting end-users to various parts of the web app and handling responses.

Response Codes:

A typical web server accepts HTTP requests from clients and then sends response codes, responses can be categorised into five different bands:

1.  Informational responses (100-199)
2.  Successful responses (200-299)
3.  Redirection messages (300-399)
4.  Client error responses (400-499)
5.  Server error responses (500-599)

The [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) gives a comprehensive overview of status codes, but the most common response codes are:

| Code                      | Description                                                                                                |
|---------------------------|------------------------------------------------------------------------------------------------------------|
| 200 OK                    | The request has succeeded, success is different for the different HTTP methods (POST, GET, etc.)           |
| 301 Moved Permanently     | The URL of the request has changed permanently, the new URL is given in the response.                      |
| 302 Found                 | The URL of the requested resource has changed temporarily                                                  |
| 400 Bad Request           | The server couldn’t understand the request due to bad syntax.                                              |
| 401 Unauthorized          | Unauthenticated attempt to access page                                                                     |
| 403 Forbidden             | The client doesn't have access rights to the content                                                       |
| 404 Not Found             | The server cannot find the resource.                                                                       |
| 405 Method not allowed    | The request method is known by the server, but is disabled.                                                |
| 408 Request Timeout       | This response is sent on idle connections by configured servers, even if the client does send any requests |
| 500 Internal Server Error | The server has encountered a situation it doesn't know now to handle                                       |
| 502 Bad Gateway           | The server whilst working with a gateway receives an invalid request.                                      |
| 504 Gateway Timeout       | The server is acting as a gateway and cannot get a response in time.                                       |

Different types of web servers:

We can spin up our own web-servers using Python, JavaScript and PHP. But there are the big 3 hosts of web applications that run 95% of web-servers on the internet.

1.  Apache
    1.  Apache (httpd) is the most common web server on the internet, it hosts around 40% of all internet websites and is pre-installed on most Linux distributions. Though you can use it on Windows and MacOS too.
    2.  Apache is generally used in combination with **PHP**, but it also supports other popular languages like **.NET, Python and Perl.** You can even use OS languages like **Bash** via **CGI.** Since there are many mods that extend Apache's functionality.
    3.  Apache is an open-source project which is highly active, is regularly patched and is well documented. This makes it ideal for startups, but it is flexible enough so that large companies also use Apache.
2.  NGINX
    1.  NGINX is the second most common webserver on the internet, it hosts around 30% of all internet services. NGNIX is good at serving many web requests with low memory and CPU load.
    2.  NGINX is very popular amongst popular websites and is free and open source too.
3.  IIS
    1.  Microsoft Internet Information Services runs around 15% of internet websites. IIS mainly runs on Windows servers and is primarily used to host web apps that use the .NET framework.
    2.  IIS is also well optimised for **Active Directory** integration and can be used to authenticate users automatically
    3.  IIS is used by big corporations mainly that run on Windows Servers or require Active Directory within their organisation.

Smaller web servers include Apache Tomcat for Java apps and Node.JS for JavaScript backends.
Requesting to a web server:

Web servers also accept various types of data within HTTP requests such as: text, JSON (JavaScript Object Notation) and binary data (i.e. during file uploads).

Once a web server receives a web request it is then responsible for routing it to its destination along with running any processes that are needed and returning the response to the user on the client side.

Using CURL to look at HTTP requests:

Using the -I flag within cURL we can receive the servers response:
![image2](../../../../_resources/image2-89.png)

We can also just use curl by default to show the source code of the website:
![image3](../../../../_resources/image3-74.png)

