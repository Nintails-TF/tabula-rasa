---
title: SQL injection UNION attacks
updated: 2023-06-04T18:22:58.0000000+01:00
created: 2023-06-03T16:49:28.0000000+01:00
date modified: Tuesday, May 21st 2024, 5:02:50 pm
---

Introduction:

SQL injections that use the **UNION** keyword differ from regular SQL injections, because they are used to retrieve data/responses from different tables in the database.

This is because the union keyword enables you to SELECT from multiple tables then append the results to a single query. The boilerplate for this is:

![image1](../../../_resources/image1-6.png)

This will return a single query result which contains:

- *A and b from table1*
- *c, d from table2*

Using the UNION keyword:

In order to use the UNION keyword, we need to meet the following conditions:

1.  The numbers of columns returned from each table must be equal.
    1.  i.e. we return 2 columns from table1 (a, b), we need to return 2 columns from table2 (c, d).
2.  The datatypes within columns must be the same.
    1.  i.e. the data from table1 and table2 are both integer values.

**To perform a UNION injection, we need the following info:**

- How many columns are returned from the original query?
  - i.e. how many columns are in *"SELECT a, b FROM table1"* in this case it is 2.
- Which columns from the original query have a suitable data type to hold the results from the injected query.

Figuring out the number of columns:

In order to perform a UNION injection, we need to first figure out the number of columns returned by our query. We have two main ways of doing this:

1.  Injecting ORDER BY clauses.
2.  Submitting UNION SELECT clauses.

Order By Method:

We would input order by clauses until we hit an error, since we can define columns using their **index** rather than their name, we can figure out how many columns are in the table. *For example:*

*SELECT a, b FROM table 1 WHERE a \> b 'ORDER BY 1--*
*SELECT a, b FROM table 1 WHERE a \> b 'ORDER BY 2--*
*SELECT a, b FROM table 1 WHERE a \> b 'ORDER BY 3--*
*Etc.*

*(Remember we need the comment \[--\] to comment out any other SQL logic that comes after our query.)*

We will know that we have reached the end of the columns when we see the following error:

***The ORDER BY position number 3 is out of range of the number of items in the select list.***

This means that the ORDER BY 3-- is out of range.

In reality, the application may not give you the same error message it may:

- Return the error in the HTTP response
- Return a generic error
- Return no error

As long as you can tell that a different response is being generated, you can infer that you have found the number of columns in the table.

Union Select Method:

Now we would input UNION SELECT Clauses whilst specifying NULL columns. We would do this via:

***SELECT a, b FROM table 1 'WHERE a \> b' UNION SELECT NULL--***
***SELECT a, b FROM table 1 'WHERE a \> b' UNION SELECT NULL, NULL--***
***SELECT a, b FROM table 1 'WHERE a \> b' UNION SELECT NULL, NULL, NULL--***

Again we would know when we have reached the limit of the table once we see an error message like:

*All queries combined using a UNION, INTERSECT or EXCEPT operator must have an equal number of expressions in their target lists.*

Again we may only see a generic error, or nothing returned. **Once the result matches the number of columns**, we will get a query with a column nulls that match the number of columns.

This may cause an additional row to be displayed in the best case, we may also get *a Nullpointerexception* error but in the worst case the response might be undiscernible from the correct/incorrect number of rows, which can make this method unreliable.

\[**On Oracle databases**, every SELECT needs to reference a table name, in this case we use **dual**, which is a built in table in every oracle database: UNION SELECT NULL FROM DUAL--\]

(Note that the reason why we use NULL here is because NULL will work with any datatype, this means the payload will work more often.)
Finding useful data types using UNION inject:

When performing an injected query, the info we generally want is in a string form. So we need to find a column that is string or that accepts string data type.

You can probe for columns that use a string data type by entering a string once you figure out the number of columns. For example:

![image2](../../../_resources/image2-5.png)

' UNION SELECT 'mr tails', NULL, NULL, NULL--

This would probe 4 columns to check for a string column. If the column is **not suitable** for strings, we would get the following error:

*Conversion failed when converting the varchar value 'a' to data type int.*

If an **error does not occur**, then we have found a column which can hold string data which we may want to retrieve from the table.

Finding meaningful data using UNION SQL injection:

Once you have figured out how many columns are in the table and where we can write strings to we can use this information to reveal information from different tables.

For example, if the server has a database named users that holds user details, we could use:

*' UNION SELECT username, password FROM users--*

To get password details about users.

Of course the crux of this challenge is actually knowing that there is a user's table that we can access. Right now, all we have is to guess the table names, but modern databases provide us ways of examining database structure.

Retrieving multiple strings within a single column:

If you only have access to a single column, you could return data by concatenating strings together, we could achieve this by using:

***' UNION SELECT username \|\| '\~' \|\| password FROM users--***

(Note that this would only work for Oracle databases, check the cheat sheet for other DB types.)

You can change the middle character as the divider.

**Use the Repeater!:**

**Making use of the repeater in BURP suite makes these injects much easier!**
