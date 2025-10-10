---
title: 'Activity:'
updated: 2023-01-21T20:49:41.0000000+00:00
created: 2023-01-21T20:45:35.0000000+00:00
---

![image1](../../../../../_resources/image1-99.png)

We first log-in, then we reload the page after clearing the trash and copy the POST into **Copy \> Copy cURL.** Giving us the following command:

curl '<http://178.128.37.153:32104/search.php>' -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0' -H 'Accept: \*/\*' -H 'Accept-Language: en-US,en;q=0.5' --compressed -H 'Referer: <http://178.128.37.153:32104/'> -H 'Content-Type: application/json' -H 'Origin: [http://178.128.37.153:32104'](http://178.128.37.153:32104') -H 'DNT: 1' -H 'Connection: keep-alive' -H 'Cookie: PHPSESSID=m86h67gnjidrh3javge73t1u4c' --data-raw '{"search":"London"}'

We then edit this to use cURL as the user-agent and search for the flag:

curl '<http://178.128.37.153:32104/search.php>' -H 'Accept: \*/\*' -H 'Accept-Language: en-US,en;q=0.5' --compressed -H 'Referer: <http://178.128.37.153:32104/'> -H 'Content-Type: application/json' -H 'Origin: [http://178.128.37.153:32104'](http://178.128.37.153:32104') -H 'DNT: 1' -H 'Connection: keep-alive' -H 'Cookie: PHPSESSID=m86h67gnjidrh3javge73t1u4c' --data-raw '{"search":"flag"}'

Thus giving us the flag:
![image2](../../../../../_resources/image2-80.png)
flag: HTB{p0\$t_r3p34t3r}
