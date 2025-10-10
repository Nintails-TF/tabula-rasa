---
title: 'Lab - SQL injection Union 2:'
updated: 2023-06-04T13:44:21.0000000+01:00
created: 2023-06-04T13:05:26.0000000+01:00
---

![image1](../../../../_resources/image1-8.png)
Method:

Firstly, we need to figure out the number of columns, as we learned from the first lab. We can find the number of
Columns using the ORDER BY method:
![image2](../../../../_resources/image2-7.png)

Which shows us we have three columns:
![image3](../../../../_resources/image3-5.png)

(as if we try to use 'ORDER+BY+4-- we get an internal server error):
![image4](../../../../_resources/image4-3.png)

Now we need to probe the four columns for one that can accept strings:

'UNION+SELECT+'mrtails',NULL,NULL--

We can test columns by placing the HTTP request into the reapeater and checking each column:
![image5](../../../../_resources/image5-2.png)

Since we get a 200 request, we know that the **2nd column** accepts string input. We can then send the requested string:
![image6](../../../../_resources/image6-2.png)

The lab is solved. Since we know that the 2nd column can accept strings.

