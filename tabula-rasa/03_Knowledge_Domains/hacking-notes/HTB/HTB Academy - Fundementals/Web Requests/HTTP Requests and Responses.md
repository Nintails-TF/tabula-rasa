---
title: 'HTTP Requests and Responses:'
updated: 2023-01-20T08:52:52.0000000+00:00
created: 2023-01-20T08:19:06.0000000+00:00
---

Introduction:
HTTP requests consist of a HTTP request and HTTP response:
1.  An HTTP request is made by the client.
2.  Then the client processes this request.
3.  Once the server receives the HTTP request it sends the HTTP response.

Structure of a HTTP Request:
![image1](../../../../_resources/image1-93.png)

This is sending a HTTP GET request to the URL: ***<http://inlanefreight.com/users/login.html>.*** The first line of any HTTP request contains three main fields "separated by spaces". These can be summarised as:
![image2](../../../../_resources/image2-74.png)

The next set of lines contains the HTTP header value pairs. These headers are used to specify various attributes of a request. The headers are have a separate line, so that the server is used to validate the request.

*HTTP version 1.X requests as clear-text. HTTP version 2.X, on the other hand requests binary data in a dictionary form.*

DevTools:

We can browse the dev tools to try and get more information, mainly we are interested in the **network** tab and filtering for certain URLs is helpful for larger pages with tons of URLs. Viewing the raw source code is also helpful.

HTTP Response:

Once the server processes our request, it sends its response. The following is an example HTTP response:
![image3](../../../../_resources/image3-63.png)

We can summarise this as:

HTTP version response contains two fields separated by spaces. The first being the HTTP version (**HTTP/1.1)** and the second denotes the *HTTP response code* **(200 OK).**

The response codes are used to determine the request's status. Then you get the response headers, just like the HTTP request.

Finally, you get the response body which is usually in HTML, but sometimes other languages can be used like JSON, or PDF.

cURL:

cURL, also allows us to show the full HTTP request, which can be helpful for pen tests or writing exploits. To view this information, you can the **-v** flag:
![image4](../../../../_resources/image4-54.png)

This gives us the full HTTP request and response. We can also use **-vvv** for even more verbose output:

