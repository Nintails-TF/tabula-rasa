* * *

## title: 'Activity:'  
updated: 2023-09-07T14:47:21.0000000+01:00  
created: 2023-09-07T13:49:47.0000000+01:00

![image1](../../../../_resources/image1-205.png)

Case 5 involves an OR SQLi vulnerability in GET parameter id. This means that in order to actually exploit this vulnerability we need to raise our level of risk.

1.  Copy the request as cURL from the **network tab** in the browser.
2.  Replace the cURL keyword with sqlmap and add the following flags
    1.  ![image2](../../../../_resources/image2-171.png)
    2.  Note that this will try to dump all data from the table, which will take a long time. We can enable different options to speed up this process.
        1.  **\-T flag5** will only enumerate the table named **flag5**.
        2.  **\--no-cast** will turn off the payload casting function
    3.  Our final flags:
        1.  ![image3](../../../../_resources/image3-136.png)

![image4](../../../../_resources/image4-111.png)

**Risk=3 is FAR slower than the default settings.**  
![image5](../../../../_resources/image5-85.png)

Case 6 involves an SQLi vulnerability in the GET parameter of col, in which col has non-standard boundaries. This means we should increase our level of level to exploit this.

1.  Copy as cURL from browser
2.  Add the following flags to the SQLMap request
    1.  ![image6](../../../../_resources/image6-61.png)

![image7](../../../../_resources/image7-54.png)

![image8](../../../../_resources/image8-47.png)

Case 7 involves a SQLi vulnerability in a GET parameter id by using a UNION query technique. Through manual testing, we find that there is **32 rows and 5 Columns**, we can then supply this to our UNION columns flag. (we use union cols is 5.)

1.  Copy as cURL from browser
2.  Add the following flags
    1.  ![image9](../../../../_resources/image9-40.png)
        1.  Union from is used to specify the table name we are interested in.  
            ![image10](../../../../_resources/image10-33.png)