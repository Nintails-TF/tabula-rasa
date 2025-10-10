---
title: Examining DBs for SQL Injections
updated: 2023-06-06T14:57:24.0000000+01:00
created: 2023-06-04T15:18:37.0000000+01:00
date modified: Friday, May 17th 2024, 5:07:23 pm
---

Listing the contents of a database:  

Most database types have a set of views called **schemas.** What these schemas do is provide information about the database.

(Note - Oracle databases don't use schema views).

We can query schemas like so:

***SELECT \* FROM information_schema.tables***

This will produce the output of:
![image1](../../../_resources/image1-11.png)

This shows us a list of every table that is inside the database and gives us some additional metadata on them.

We can also view each column in a specific table by using the following query:

***SELECT \* FROM information_schema.columns WHERE table_name = 'Users'***

*Output:*
![image2](../../../_resources/image2-10.png)

This is valuable as it can reveal potentially interesting or useful columns, like credentials or columns that can accept strings so that a UNION injection can be performed.

Listing the contents of a database - ORACLE:

The queries we need are a little different on Oracle databases. To list all tables:
***SELECT \* FROM all_tables***

To list all columns of a specific table use:
***SELECT \* FROM all_tab_columns WHERE table_name = 'USERS'***
Examining DBs for SQL Injections:
04 June 2023
15:18

Introduction:

Before we can exploit SQL injection vulnerabilities we often need information on the database itself. For example: the database version and type along with the contents of the database and the columns it contains.

*I.e. Before we can exploit something, we need to understand it.*

Querying databases:

Different databases have different methods and syntax for writing queries, this is why we often write queries to check the version of a database first. Common queries for popular database software is:

| Database Type    | Query                     |
|------------------|---------------------------|
| Microsoft, MySQL | SELECT @@version          |
| Oracle           | SELECT \* FROM v\$version |
| PostgreSQL       | SELECT version()          |

We could perform a UNION attack like so:

*' UNION SELECT @@version--*

This could return:

*Microsoft SQL Server 2016 (SP2) (KB4052908) - 13.0.5026.0 (X64) Mar 18 2018 09:11:49 Copyright (c) Microsoft Corporation Standard Edition (64-bit) on Windows Server 2016 Standard 10.0 \<X64\> (Build 14393: ) (Hypervisor)*

Which would tell us:

- The database is ran by a Microsoft SQL server.
- The server is running "Microsoft Corporation Standard Edition"
- The Windows server is 2016 version 10.0
