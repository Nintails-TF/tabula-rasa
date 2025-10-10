---
title: 'SQLMap on HTTP Requests:'
updated: 2023-09-01T11:27:23.0000000+01:00
created: 2023-08-28T16:02:47.0000000+01:00
---

Introduction:

SQLMap has numerous options and switches which can be used for HTTP requests. In most cases, **SQLMap is a valuable tool as it catches simple mistakes** - like proper cookie values, overly-complicated setup and other common misconfigurations.

Curl Commands:

The easiest way to use SQLMap is to open up devtools and to copy a request as **cURL**. We then can use **SQLMap** in a similar way to **cURL**, they are identical in this way, so:

cURL:
![image1](../../../../_resources/image1-201.png)

SQLMap:
![image2](../../../../_resources/image2-167.png)

However, when we test using SQLMap, we need to provide it with a parameter to scan. Or enable options for **automatic parameter finding (--crawl, --forms, -g).**

GET/POST Requests:

Within SQLMap we can define **GET** parameters using the **-u/--url** flags. If we want to test **POST** data, we need to use the **--data** flag:
![image3](../../../../_resources/image3-132.png)

This would cause SQLMap to test both the **uid** and the **name** parameter. If we know that a certain parameter is vulnerable to SQLi, we can narrow our scan using the **-p** flag (e.g. **-p uid**). We can also mark the parameter using an **asterisk:**
![image4](../../../../_resources/image4-107.png)

Full HTTP Requests:

If we need to specify a more complex HTTP request with lots of different header values and larger amounts of POST data. We can use the **-r** flag - which is the request file option in which a whole HTTP request will be loaded from file. A common way of doing this is via a web proxy (e.g. BURP/ZAP):
![image5](../../../../_resources/image5-83.png)

We can right-click and **copy to file.** Then we can use this request inside of **SQLMap**:
![image6](../../../../_resources/image6-59.png)

*Note that we can perform the same post parameter specification using asterisks within our custom request file.*
Custom SQLMap Requests:

There are few useful flags and switches we can enable for SQLMap that can help us craft more custom requests to tests for SQLi.

- **--cookie**
  - This will enable us to set a session cookie
    - ![image7](../../../../_resources/image7-52.png)
- **-H/--header**
  - This enables us to set a HTTP header:
    - ![image8](../../../../_resources/image8-45.png)
  - We can perform similar definitions of header values using **--host, --referrer** and **-A/--user-agent.**
- **--random-agent**
  - This will randomly pick a **User-Agent** header value from a list of values from a database.
  - This is important since many browsers will block all traffic to the SQLMap default user-agent.
- --mobile
  - This will imitate a smartphone using a header value.
- --method
  - Allows us to define a HTTP method (e.g. GET, POST, PUT, INCLUDE, etc.)

Do note that SQLMap by default will only target HTTP parameters for SQLi vulnerabilities. We can also specify to test for injections in the cookie field using the **asterisk marker:**

***e.g. --cookie="id=1\*"***

Custom HTTP Requests:

SQLMap also supports testing **JSON and XML** formatted data. We can simply include the information inside of the POST request using the **-r** flag again:
![image9](../../../../_resources/image9-38.png)

