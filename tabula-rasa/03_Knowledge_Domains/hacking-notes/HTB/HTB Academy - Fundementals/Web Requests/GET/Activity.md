---
title: 'Activity:'
updated: 2023-01-20T20:05:43.0000000+00:00
created: 2023-01-20T19:52:55.0000000+00:00
---

![image1](../../../../../_resources/image1-97.png)

We first send a request in the browser, then copy the PHP request as cURL:
![image2](../../../../../_resources/image2-78.png)

This gives us the following command:
curl '<http://165.227.231.233:31413/search.php?search=London>' -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0' -H 'Accept: \*/\*' -H 'Accept-Language: en-US,en;q=0.5' --compressed -H 'Referer: <http://165.227.231.233:31413/'> -H 'DNT: 1' -H 'Authorization: Basic YWRtaW46YWRtaW4=' -H 'Connection: keep-alive'

Trying to execute this command gives us:
![image3](../../../../../_resources/image3-66.png)

Since our **user-agent** is Mozilla and not cURL

We can trim the fat from this command and use cURL, since the **user-agent** will default to cURL:
curl '<http://165.227.231.233:31413/search.php?search=London>' -H 'Authorization: Basic YWRtaW46YWRtaW4=' -H 'Connection: keep-alive'
We then change the search term to get the flag:
![image4](../../../../../_resources/image4-57.png)

