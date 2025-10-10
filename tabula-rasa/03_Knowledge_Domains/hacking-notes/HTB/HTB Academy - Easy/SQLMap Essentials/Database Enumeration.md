* * *

## title: 'Database Enumeration:'  
updated: 2023-09-11T12:36:49.0000000+01:00  
created: 2023-09-07T14:47:49.0000000+01:00

## Introduction:

Database enumeration is a central part of a SQL injection attack, which is done right after successful detection and confirmation of a vulnerability. It is the step in which we look up database information and we **exfiltrate** (retrieve) all data from the database.

This enumeration is the reason why we have password lists like rockyou.txt, since it is necessary to exfiltrate data from these vulnerable databases so that we can prove that a vulnerability exists.

## SQLMap Data Exfiltation:

SQLMap has a predefined set of all queries from all supported DBMSes. Where each query payload will grab all data from the desired database. We can see this in **queries.xml** for an example of queries for a **MySQL DBMS.**

So whenever a user wants information from the DBMS the call apon this **queries.xml** file, example of queries include:

- **\-banner** will execute **VERSION()**
- **\--current-user** will execute **CURRENT\_USER()**

But how would we get call usernames? We use **inband** for non-blind SQLi (*Uinion-query and error-based*). This is because we will get the usernames inside the query response.

We would use **blind** in all blind SQLi attacks *(time-based blind or Boolean-based blind),* since we will need to get the data row-by-row, column-by-column, or bit-by-bit.
***
## Basic DB Data Enumeration

When SQLMap detects a SQLi vulnerablitiy, we can start to enumerate basic info from the database such as: 

- **--hostname**
- **--current-user**
	- Returns username of DB manager.
- **-current-db**
	- Returns the current DB name.
- **passwords**
	- Returns password hashes.
- **--is-dba**
	- Checks if the current user as admin (DBA) rights

What we usually want to start with is the following:
`sqlmap -u "http://www.example.com/?id=1" --banner --current-user --current-db --is-dba`

*We may see that user's can be called **root.** A root user in the context of a DBMS means that they can do anything within the DB system. But they cannot use OS priviledges beyond the basics.*

***
## Table Enumeration:
Once we find a database name (i.e. **testdb** in this case). We want to start looking at the tables using the **--tables** flag. *We need to make sure to specify the DB name e.g. **-D testdb***. For example:

`sqlmap -u "http://www.example.com/?id=1" --tables -D testdb`

Once we find interesting looking table names, we can **dump** them by specifiy the table name:

`sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb`

By default, the **--dump** flag will output the table as a CSV. (e.g. users.csv). Alternatively, we can use the flag **--dump--format** to dump the table in a HTML or SQLite format. This enables us to investigate the DB in a SQLite DBMS.

### Table/Row Enumeration:

When dealing with large tables with lots of columns/rows. We can specify column names using the **-C** flag:

`sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb -C name,surname`

We can also use the **--start** and **--stop** options, which will tell SQLMap what rows we want to start grabbing. e.g. So that we start from entry 2 to entry 3.

`sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb --start=2 --stop=3`
***
## Conditional Enumeration:


