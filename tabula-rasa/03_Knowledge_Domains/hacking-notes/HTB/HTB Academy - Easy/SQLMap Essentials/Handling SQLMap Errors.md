---
title: 'Handling SQLMap Errors:'
updated: 2023-09-04T10:25:03.0000000+01:00
created: 2023-09-01T11:58:17.0000000+01:00
---

Introduction:

We may face some errors in using SQLMap, or using it with HTTP requests. The steps we should take to debug the program is to:

1.  Display Errors
2.  Store Traffic
3.  Look at verbose output
4.  Send SQLMap traffic through a web proxy

Displaying Errors:

We can use the **--parse-errors** flag to parse any DBMS (Database Management System) errors (if there are any) and show them in our run of the program:
![image1](../../../../_resources/image1-203.png)

This gives us information from the DBMS which enables us to have more clarity in fixing the issue.

Storing the traffic:

We can use the **-t** flag to store the all the traffic content to and from SQLMap to an external file:
![image2](../../../../_resources/image2-169.png)

This enables us to manually look at HTTP requests and we can investigate and isolate what is causing the issue.

*Note that it usually makes sense to have the traffic file stored in an impermanent place, e.g. tmp or to overwrite the same file to avoid clogging up your file system.*
Verbose Output:

We can use the **-v** flag for verbose output. This will give us a much more detailed breakdown on what SQLMap is doing:
![image3](../../../../_resources/image3-134.png)
*Note that verbosity levels range from 1-6. 6 being the most verbose.*

What using verbose output enables us to do, is that it prints all errors and full HTTP requests to the terminal so we can follow along step-by-step to see what is going on with SQLMap.

Using Proxy:

Finally, we can use the **--proxy** flag to route our traffic via a proxy - like Burp or ZAP. This enables us to investigate all requests between the target and SQLMap:
![image4](../../../../_resources/image4-109.png)

