---
title: 'Activity:'
updated: 2023-09-01T11:57:54.0000000+01:00
created: 2023-09-01T11:28:28.0000000+01:00
---

![image1](../../../../_resources/image1-202.png)

Case \#2 appears to be a SQLi that uses a vulnerable POST request.

1.  Copy the POST request to cURL (case2.php)
    1.  ![image2](../../../../_resources/image2-168.png)
2.  Use SQLMap
    1.  ![image3](../../../../_resources/image3-133.png)
3.  We can see from the output that the **id** parameter is vulnerable to many different types of SQLi
    1.  ![image4](../../../../_resources/image4-108.png)
    2.  We can just use Boolean-based blind SQLi in this example
4.  **We can use the commands --batch and --dump** to get all the output into our terminal and avoid user input
    1.  We see a second table which stores our flag:
        1.  ![image5](../../../../_resources/image5-84.png)

![image6](../../../../_resources/image6-60.png)
Case \#3 appears to be SQLi with a cookie field.

1.  Copy the GET request to cURL (case3.php)
2.  Use SQL map and configure our cookie
    1.  ![image7](../../../../_resources/image7-53.png)
3.  We can see that our flag is located in the table **flag3**
    1.  ![image8](../../../../_resources/image8-46.png)
![image9](../../../../_resources/image9-39.png)
Case \#4 involves SQLi of JSON data.

1.  Copy the **xhr** request into cURL.
2.  Use SQLMap
    1.  We can see that the JSON data is stored in **--data-raw:**
        1.  ![image10](../../../../_resources/image10-32.png)
3.  Remember to include --batch to skip user input and --dump to dump all the info to terminal
    1.  ![image11](../../../../_resources/image11-25.png)
