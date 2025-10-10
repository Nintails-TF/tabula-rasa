---
title: 'Sequel:'
updated: 2022-09-10T12:53:13.0000000+01:00
created: 2022-09-10T12:14:58.0000000+01:00
---

During our scan, which port running mysql do we find?:

*Using nmap we find that mysql is running on port 3306.*

What community-developed MySQL version is the target running?:

*It is running MariaDB.*

What switch do we need to use in order to specify a login username for the MySQL service?:

*Using -u we can specify login details.*

Which username allows us to log into MariaDB without providing a password?:

*Root is the username that allows us to log into MariaDB without a password.*

What symbol can we use to specify within the query that we want to display everything inside a table?:

*The \* symbol can be used.*

What symbol do we need to end each query with?

A semi-colon (;).

Getting the flag:

Firstly, we need to access this service via the console. We can do this using the mysql command like so:

![image1](../../../../../_resources/image1-57.png)

This allows us to login into the MariaDB server. Now we need to navigate to the flag using SQL queries, helpful queries include:

- SHOW DATABASES; - This gives us a list of all databases
- USE \[Dbname\]; - This sets the active database.
- SHOW TABLES; - This gives us a list of all tables in the active database
- SELECT \* FROM \[TableName\] - This gives us all information in the table.

Thus we are able to navigate to the flag:
7b4bec00d1a39e3dd4e021ec3d915da8

