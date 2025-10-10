---
title: 'Code Analysis:'
updated: 2023-08-06T03:13:00.0000000+01:00
created: 2023-08-06T02:38:56.0000000+01:00
---

Code Analysis:

Once we deobfuscate code, we need to still understand what it does, for example:
![image1](../../../../_resources/image1-164.png)

Let look at each line of this function.

1.  We have the variable *xhr* which creates an object of XMLHttpRequest.
    1.  What is XMLHttpRequest? Google it!
        1.  [**According to the MDN**](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest), We see that this request is used send web requests and gather data from a URL.
2.  URL is the variable in which the XMLHttpRequest is going to get data.
    1.  We know that it is on the same domain, since no other domain was specified.
3.  Now we see an HTTP POST request going to the /serial.php URL
4.  Finally, we send a request to the PHP file - but with only NULL data.

We now know that this function performs a POST request that is supposed to **generate a serial.** But this feature seems depreciated but the function remains.

We can now try to replicate this functionality to see if the data is handled on the server side when sending a POST request. If it is this is a potential vulnerability that can uncover unreleased functionality.

Sending our own POST request:

We can use **cURL** to send our own modified POST request. We can do this via:
![image2](../../../../_resources/image2-134.png)

Where:
- -X
  - This is our request method - POST - in this event
- -d
  - Is the parameter we want to send using the POST request.

