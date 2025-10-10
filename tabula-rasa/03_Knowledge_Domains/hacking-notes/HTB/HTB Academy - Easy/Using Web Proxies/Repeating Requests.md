---
title: 'Repeating Requests:'
updated: 2023-08-10T12:14:37.0000000+01:00
created: 2023-08-10T09:58:09.0000000+01:00
---

Introduction:

Repeating requests is a really important tool as it enables us to quickly make changes to a certain request we are interested in, then check the results of it - did the request go through, etc.

Burp - Proxy History:

We can navigate to **proxy\>HTTP History** to see previous requests, we can then send them to the repeater for further usage.
![image1](../../../../_resources/image1-172.png)

Burp has an advantage here as you can examine both the original and modified request.

Burp - Repeating Requests:

Once we find a request we want to replace, we can use **CTRL+R** to send it to the **repeater** tab. We then can click send to send the request.

We can also right-click the request and **change the request method** to POST or GET without needing to re-write the request by hand.

**Finding the 2nd flag:**
1.  List files
    1.  ip=1;ls+-a;
    2.  ![image2](../../../../_resources/image2-141.png)
    3.  A better method of doing this is using **-la** since you can see what files are directories and what are just plain files.
        1.  ![image3](../../../../_resources/image3-107.png)

**COMMAND PIPING DOESN'T WORK, USE ; TO SPLIT COMMANDS:**
![image4](../../../../_resources/image4-84.png)
(Remember that / will take you to root and we can see the flag).
![image5](../../../../_resources/image5-65.png)

**Catting our flag:**
![image6](../../../../_resources/image6-44.png)
![image7](../../../../_resources/image7-38.png)

ZAP - Proxy History:

We can either look at the ZAP HUD and its **history tab**, or we can look at ZAPs main UI at the history tab:

![image8](../../../../_resources/image8-32.png)

We can use filters to search for specific requests or URLs:
![image9](../../../../_resources/image9-27.png)

*Note that both tools maintain a **WebSocket history too**. These are useful to check all connections that are initiated by the web app even after being loaded like any asynchronous updates and data fetching.*

*This is normally reserved for more advanced pen testing though.*

Zap - Repeating Requests:

We can do this via right clicking on a history tab and selecting **Open/Resend with request editor** or we can also press **CTRL + W** to open the request in the main requester:
![image10](../../../../_resources/image10-22.png)

The ideal view for repeating would be **full view** and **request and response side by side.**

We can achieve the same thing in the ZAP HUD, by using the history tab and clicking on any request that we can then replay in **console or browser.**
![image11](../../../../_resources/image11-17.png)

Alternative method:

We can use find to get our flag:
![image12](../../../../_resources/image12-12.png)
*(Search from root and look for files with the name flag.txt)*

We can see both flags:
![image13](../../../../_resources/image13-11.png)

Gives us the flag:
![image14](../../../../_resources/image14-9.png)
