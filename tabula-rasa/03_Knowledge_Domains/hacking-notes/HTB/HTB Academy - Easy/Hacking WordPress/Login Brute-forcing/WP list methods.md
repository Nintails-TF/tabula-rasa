---
title: 'WP list methods:'
updated: 2023-07-20T01:36:43.0000000+01:00
created: 2023-07-20T01:22:48.0000000+01:00
---

![image1](../../../../../_resources/image1-129.png)

We need to use the xmlrpc to find what kinds of methods we can execute. <https://codex.wordpress.org/XML-RPC/system.listMethods> looks like a good start.

curl 94.237.59.206:37244/xmlrpc.php -X POST -d "\<methodCall\>\<methodName\>system.listMethods\</methodName\>\<params\>\</params\>\</methodCall\>"

This does return all methods, but doesn't count them:
![image2](../../../../../_resources/image2-105.png)

If I can count the occurrences of "\<value\>\<string\>" string, I should be able to count the number of methods. I think I can use grep for this:

curl 94.237.59.206:37244/xmlrpc.php -X POST -d "\<methodCall\>\<methodName\>system.listMethods\</methodName\>\<params\>\</params\>\</methodCall\>" \| grep -c "\<value\>\<string\>"
![image3](../../../../../_resources/image3-84.png)

We use -c to count the occurrences of the string and there is **80 methods.**
(alternatively, we could use wc to count the occurrences.)

