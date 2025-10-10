---
title: Blind SQL Injections
updated: 2023-06-21T15:10:04.0000000+01:00
created: 2023-06-06T16:41:53.0000000+01:00
date modified: Tuesday, May 21st 2024, 5:02:45 pm
---

Introduction:

A blind SQL injection is a type of SQL injection that we can use when we do not have any HTTP response indicating the results of an SQL query or database errors.

This makes our UNION attacks ineffective, since we need to know the names of tables and columns. Though it is still possible to exploit using a SQL injection, but we need different techniques.

Blind Injection By looking at Cookie responses:

If we have an application that uses a tracking cookie to check if we are visiting the website for the first time we can exploit this feature, if we have a tracking cookie:

*Cookie: TrackingId=u5YD3PapBcR4lN3e7Tj4*

The web application then uses the following query in order to check if the user is known or that they are a new user:

***SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'u5YD3PapBcR4lN3e7Tj4'***

This SQL statement is vulnerable to an injection as it returns a **Welcome Back** message if the user is known. We then can use a blind SQL injection in order to grab information from the database using this feature alone. Since we can validate true/false statements.

**The way we do this is via**:
![image1](../../../_resources/image1-16.png)

We add on another statement, If it is true - then the welcome back message is returned. Otherwise, no welcome back message would be returned. **We can then use this to construct queries that test 1 character at a time, then validate the result.**

We can use this to:

1.  Figure out table names
    1.  i.e. we can validate if a table named "Admin" exists
2.  Figuring out the data inside fields.
    1.  i.e. if we perform ***xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) \> 'm***
    2.  And we receive a welcome back response, then this indicates that there is a user named "administrator" and that the first character of the user name is greater than m.
    3.  **xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) \> 't**
    4.  And we check that the password firsts character is greater than t
    5.  xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) = 's
    6.  Finally, we know the first character from the admins username is s.

![image2](../../../_resources/image2-15.png)

