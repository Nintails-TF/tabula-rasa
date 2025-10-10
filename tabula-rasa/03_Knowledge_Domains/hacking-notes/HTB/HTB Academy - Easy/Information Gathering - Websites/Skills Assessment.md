---
title: Skills Assessment
updated: 2023-08-05T18:14:37.0000000+01:00
created: 2023-08-05T17:18:02.0000000+01:00
date modified: Sunday, September 1st 2024, 9:29:17 am
---

![image1](../../../../_resources/image1-160.png)
Introduction:

We need to perform information gathering using both active and passive enumeration. Mainly against GitHub.

![image2](../../../../_resources/image2-130.png)

1.  We can find this information using a **WHOIS** lookup.
    1.  ![image3](../../../../_resources/image3-100.png)
    2.  ![image4](../../../../_resources/image4-78.png)

![image5](../../../../_resources/image5-60.png)

1.  We can use **dig** to look at all the mail servers
    1.  ![image6](../../../../_resources/image6-39.png)
    1.  We can use whatweb to look at this:
        1.  ![image7](../../../../_resources/image7-33.png)

2.  ![image8](../../../../_resources/image8-29.png)

![image9](../../../../_resources/image9-25.png)

1.  We can use **crt.sh** to passively get info on any sub-domains that have triage in them
    1.  ![image10](../../../../_resources/image10-20.png)
2.  We can use grep to filter this data and look for anything with triage in it
    1.  ![image11](../../../../_resources/image11-15.png)

