* * *

## title: 'HTTP Headers:'  
updated: 2023-01-20T10:03:37.0000000+00:00  
created: 2023-01-20T09:01:33.0000000+00:00

Introduction:

A HTTP header pass information between client and server, some headers are only used with either requests or responses, whilst some other general headers are common to both.

Headers can have one or many values, we can divide them into the following categories:

1.  **General Headers**
2.  **Entity Headers**
3.  **Request Headers**
4.  **Response Headers**
5.  **Security Headers**

General Headers:

General headers are used in HTTP request and responses. They contain info that **describes the message rather than its contents.** They contain the following information:

![image1](../../../../_resources/image1-94.png)

Entity Headers:

Similar to general headers, **Entity Headers** can be **common to both the request and response**. These headers are used to **describe the content**. They are usually found in responses and POST or PUT requests:  
![image2](../../../../_resources/image2-75.png)

cURL with headers:

We can use the **\-I** flag to send a HEAD request and only display the response headers. We can also use a **\-i** flag to display the headers and the HTML code. For example:  
![image3](../../../../_resources/image3-64.png)

Similarly, we can use the **\-H** flag to set request headers. Some headers like the **user-agent** or **Cookies** headers have their own flags. We can set up our **user-agent** like so:  
![image4](../../../../_resources/image4-55.png)  
*(This makes the server believe we are a Mozilla \[Firefox\] client rather an a cURL client).*

Request Headers:

The clients sends **Request Headers** in a HTTP transaction. These headers are **used in an HTTP request and do not relate to the content of the message.** The following headers are commonly seen in HTTP requests:

![image5](../../../../_resources/image5-42.png)

Response Headers:

Response Headers can be used **in a HTTP response and do not relate to the content.** Certain response headers such as **Age, Location** and **server** are used to provide more context on the response, these are the most common responses:  
![image6](../../../../_resources/image6-31.png)

Security Headers:  
Finally, we have **Security Headers**. With the increase in web browser and web attackers, certain headers are used to enhance security. HTTP security headers are **a class of response headers used to specify certain rules and polices:**  
![image7](../../../../_resources/image7-25.png)

More DevTools:

We can use dev tools inside the **network** tab so that we can view header details, we can check cookies too.