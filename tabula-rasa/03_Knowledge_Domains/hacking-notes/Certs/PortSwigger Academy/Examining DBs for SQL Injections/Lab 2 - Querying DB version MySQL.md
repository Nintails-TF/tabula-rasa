---
title: Lab 2 - Querying DB version MySQL
updated: 2023-06-06T12:38:02.0000000+01:00
created: 2023-06-04T18:32:33.0000000+01:00
---

![image1](../../../../_resources/image1-13.png)
Bringing it all together:

Now we know that there are two columns, we can execute our UNION attack:
***'+UNION+SELECT+@@version,+NULL#***

![image2](../../../../_resources/image2-12.png)

And now we have the version of the database.
Similar to lab 1, but this time we are using MySQL queries. Taking our final query from lab 1, we can modify it:

***'+UNION+SELECT+BANNER,+NULL+FROM+v\$version--***
**'+UNION+SELECT+@@version**

The important change from Oracle to MySQL/Microsoft DBs, is that we don't need to specify a table name like we did with the Oracle **dual** keyword, we can just have a SELECT statement.

Firstly, we can check that the number of columns are two using:
*'+UNION+SELECT+'abc','def'--*

**TRAP:** Note that the comment system works differently on MySQL/Microsoft DBs. We should use a \# instead of a --. Whilst we can use -- with a space in MySQL, using hashtags just makes it easier for SQL injections.
![image3](../../../../_resources/image3-9.png)

Now we can check that the columns can take text:
![image4](../../../../_resources/image4-6.png)

**TRAP:** Don't forgot that there is a second column, we need to include it as a NULL value for our query to execute:
'+UNION+SELECT+@@version,+NULL#
