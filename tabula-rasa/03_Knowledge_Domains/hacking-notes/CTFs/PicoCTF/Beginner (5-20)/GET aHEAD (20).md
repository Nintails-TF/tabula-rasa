---
title: 'GET aHEAD (20):'
updated: 2022-03-02T12:29:59.0000000+00:00
created: 2022-03-02T11:50:46.0000000+00:00
---

![image1](../../../../_resources/image1-25.png)![image2](../../../../_resources/image2-23.png)![image3](../../../../_resources/image3-19.png)

Following the guide here: <https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic>  

We have gotten the HTTP history of the page.

![image4](../../../../_resources/image4-14.png)

We can see that choosing red sends the index.php using get and that choosing blue sends index.php using POST.

![image5](../../../../_resources/image5-8.png)

![image6](../../../../_resources/image6-4.png)

Using the burp suit we can intercept the PHP request and change it. However, what do we change is the question?

Looking at the title, it refers to the "HEAD" which is a way of getting data from PHP.
<https://www.w3schools.com/tags/ref_httpmethods.asp>

If we intercept the Post or get request and then change it to a head request, we get the flag!
![image7](../../../../_resources/image7-3.png)

![image8](../../../../_resources/image8-2.png)
