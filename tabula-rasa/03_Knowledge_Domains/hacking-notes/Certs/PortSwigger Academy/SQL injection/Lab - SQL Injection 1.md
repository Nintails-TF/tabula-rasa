---
title: 'Lab - SQL Injection 1:'
updated: 2023-01-05T19:26:00.0000000+00:00
created: 2023-01-05T19:13:26.0000000+00:00
---

![image1](../../../../_resources/image1-4.png)

First we need to launch BURP so we can look at the traffic that is being sent to the server and the client, we then need to modify the query to give the desired outcome - showing released and unreleased products.

For this we need to modify the category parameter with our SQL injection:
![image2](../../../../_resources/image2-3.png)

We change a normal request to:
![image3](../../../../_resources/image3-2.png)

Which gives us access to unreleased products and completes the lab:
![image4](../../../../_resources/image4-1.png)

This Lab is an example of using a SQL query to retrieve hidden data.
