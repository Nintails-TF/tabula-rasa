---
title: Lab 1 - Querying Oracle DB version
updated: 2023-06-06T12:23:18.0000000+01:00
created: 2023-06-04T18:32:30.0000000+01:00
---

![image1](../../../../_resources/image1-12.png)

To clear this lab we can use a UNION attack along with the corresponding query for Oracle to get the database version. We can submit the following query via the category field:

*'UNION+SELECT+\*+FROM+v\$version--*

**TRAP:** Oracle databases need a valid database name. We need to include the **dual** keyword so that we can look at all the tables. Our query becomes:

*'UNION+SELECT+\*+FROM+dual+v\$version--*

**TRAP:** We don't know if the column we are querying can actually accept a string input, so we need to check first if a column can take a string, then execute the query in a column that takes strings.

We can use the following query to check this:

*'UNION+SELECT+'abc','def'+FROM+dual--*

*Output:*
![image2](../../../../_resources/image2-11.png)
*(The reason why we use two columns here is because the product descriptions have two columns.):*
Bringing it all together:

Now we know both columns can accept string, we can input our payload into either and make the other blank:

***'+UNION+SELECT+BANNER,+NULL+FROM+v\$version--***
(Note that you can move the BANNER keyword to either column and the SQL payload will still work.)

***What does BANNER mean in Oracle and why do we use it here?:***

*We need to use the BANNER keyword in order to display the output from **v\$version.***
*(Oracle Reference: <https://docs.oracle.com/en/database/oracle/oracle-database/21/refrn/V-VERSION.html>)*

(Note that you can move the BANNER keyword to either column and the SQL payload will still work.)

This should display the database version inside the description column.
![image3](../../../../_resources/image3-8.png)

\[Note that BANNER_FULL doesn't work since the database is Oracle version 11g, not 18c.\]
