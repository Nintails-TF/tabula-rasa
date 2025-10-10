---
title: 'Lab - SQL injection Union 1:'
updated: 2023-06-04T13:13:41.0000000+01:00
created: 2023-06-04T07:54:27.0000000+01:00
---

![image1](../../../../_resources/image1-7.png)

We are placed onto a corporate website in which we need to determine how many columns are in the product table:
![image2](../../../../_resources/image2-6.png)

Every time we filter by using a category, we see that the get header filters for certain types of gifts, lets try an manipulate this to see the number of columns:
![image3](../../../../_resources/image3-4.png)

We then need to look for an error message.

Alternative Route:

We can use the ORDER BY method too:
![image4](../../../../_resources/image4-2.png)

'ORDER+BY+3--

Which gives the same result.

Issues:

Note that:
![image5](../../../../_resources/image5-1.png)

Will not work, since you cannot have spaces inside your request, we need to use:
![image6](../../../../_resources/image6-1.png)

**TRAP:** Remember to include the singe quote ', otherwise the SQL injection will not work!

Using the union select method:
![image7](../../../../_resources/image7-1.png)
On the website, we get the error of:
![image8](../../../../_resources/image8.png)

We then keep adding NULLs until we get a different response
![image9](../../../../_resources/image9.png)

category='UNION+SELECT+NULL,NULL,NULL--

This doesn't give us an internal error:
![image10](../../../../_resources/image10.png)

Upon a refresh, the website updates to:
![image11](../../../../_resources/image11.png)
Now we know that the number of columns in which the table contains is 3.
