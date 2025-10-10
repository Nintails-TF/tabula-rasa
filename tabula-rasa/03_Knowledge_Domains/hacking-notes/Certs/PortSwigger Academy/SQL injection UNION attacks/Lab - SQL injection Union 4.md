---
title: 'Lab - SQL injection Union 4:'
updated: 2023-06-04T18:30:07.0000000+01:00
created: 2023-06-04T15:30:49.0000000+01:00
---

3 - Exfiltrating Data:

Now that we know that we have 2 columns and that the 2nd column takes string input, we can
Inject a UNION statement to get the username and password from **users:**
![image1](../../../../_resources/image1-10.png)

*'UNION+SELECT+NULL,username+\|\|':'\|\|+password+FROM+users--*

*This is the first column that we need to select, We then place our output in the second column by using a comma to break the columns apart.*

**We get the following credentials:**

1.  wiener:tycejb5arci5elzvm5kk
2.  administrator:2f07u3pnfqtekd3q510h
3.  carlos:8s5ilxloc5d6uvle186u

We can then log in as an admin:

![image2](../../../../_resources/image2-9.png)

![image3](../../../../_resources/image3-7.png)

In this lab, we need to retrieve all usernames and passwords from the users table. It involves all the steps from the previous labs.

1.  First we need to figure out the number of columns
2.  Then we need to figure out a column which accepts strings
3.  Finally, we need to retrieve the username and password columns from the users table.

1 - Finding the number of columns:

We will use the ORDER BY method:
![image4](../../../../_resources/image4-5.png)

*'ORDER+BY+2--*

Since we get an internal service error at 3, this means that we have **2 columns.**

2 - Finding out which column takes strings.

We then use our UNION clause + some text to check which column can accept strings:
![image5](../../../../_resources/image5-3.png)

*'UNION+SELECT+NULL,'a'--*

We get a 200 response here, meaning that the **2nd column accepts strings.**

(**TRAP:** Note that using "a" will **NOT WORK**, you need to use single quotation marks).
