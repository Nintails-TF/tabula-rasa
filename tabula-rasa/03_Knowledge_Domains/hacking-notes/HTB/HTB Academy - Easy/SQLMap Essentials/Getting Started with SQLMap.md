---
title: 'Getting Started with SQLMap:'
updated: 2023-08-28T09:44:44.0000000+01:00
created: 2023-08-28T09:05:38.0000000+01:00
---

Introduction:

Upon starting **SQLMap**, the first step is looking at the help messages to see what features the tool has, in this event, SQLMap has two levels of help - **Basic listing** using the -h flag:

![image1](../../../../_resources/image1-200.png)

And the **advanced listing** using the -hh flag:
![image2](../../../../_resources/image2-166.png)

SQLMap also has a [wiki](https://github.com/sqlmapproject/sqlmap/wiki/Usage).

Basic Usage:

For example, if we have a webpage that uses **GET** to accept user input (e.g. id), we can check if the web page is affected by the SQL injection vulnerability to try and we can try exfiltrate as much data as possible. An example of PHP code would be:

![image3](../../../../_resources/image3-131.png)

If error reporting is enabled for the vulnerable SQL query the database error will be returned in the response of the web-app. So we can easily recognise a web app vulnerable to SQLi:
![image4](../../../../_resources/image4-106.png)
Running the attack using SQLMap:

To run a similar attack in SQLMap we would simply need to supply the URL to SQLMap:
![image5](../../../../_resources/image5-82.png)

*The **--batch** flag is used to avoid asking us for user input and to just use defaults for it instead. We can also use the **--update** flag to get the latest version of SQLMap.*

