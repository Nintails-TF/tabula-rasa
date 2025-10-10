---
title: 'HTTP Methods and Codes:'
updated: 2023-01-20T19:12:38.0000000+00:00
created: 2023-01-20T10:04:59.0000000+00:00
---

Introduction:

In the HTTP protocol, several request methods allow the browser to send information, forms, or files to the server. These methods are used to tell the server how to process what we send.

We have various request methods which contain the HTTP response code, For example, the most common methods are:
![image1](../../../../_resources/image1-95.png)
*(Full list of HTTP request methods:* <https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods>)

Note that most web apps use the **GET** and **POST** methods. Any web apps that use REST APIs we can also use **PUT** and **DELETE**.
Response Codes:
Http status code are used to tell the client the status of their request. A HTTP server can return 5 main types of response codes:
- ***1xx** - Provides information that doesn't affect the processing of the request.*
- ***2xx** - Returned when a request succeeds.*
- ***3xx** - Returned when the server redirects the client.*
- ***4xx** - Returned when an improper requests **from the client**. For example, requesting a resource that doesn't exist.*
- ***5xx** - Returned when there is some problem **with the HTTP server.***

The following are the commonly seen example from each of the above HTTP method types:
![image2](../../../../_resources/image2-76.png)
