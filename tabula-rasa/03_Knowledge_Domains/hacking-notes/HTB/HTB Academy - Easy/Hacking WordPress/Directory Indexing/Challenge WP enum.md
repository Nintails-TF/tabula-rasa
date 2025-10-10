---
title: 'Challenge WP enum:'
updated: 2023-07-19T21:20:39.0000000+01:00
created: 2023-07-19T20:48:34.0000000+01:00
---

![image1](../../../../../_resources/image1-126.png)

We can enumerate the core wp version using cURL:
curl -s -X GET <http://83.136.251.112:36520/> \| grep '\<meta name="generator"'
![image2](../../../../../_resources/image2-102.png)

We can enumerate wp-plugins using:
curl -s -X GET <http://83.136.251.112:36520/> \| sed 's/href=/\n/g' \| sed 's/src=/\n/g' \| grep 'wp-content/plugins/\*' \| cut -d "" -f2
![image3](../../../../../_resources/image3-82.png)

We can enumerate wp-themes using:
curl -s -X GET <http://83.136.251.112:36520/> \|sed 's/href=/\n/g' \| sed 's/src=/\n/g' \| grep 'themes' \| cut -d"'" -f2
![image4](../../../../../_resources/image4-66.png)

We can look inside the plugins:
<http://94.237.59.206:48763/wp-content/plugins/photo-gallery/>
<http://94.237.59.206:48763/wp-content/plugins/mail-masta/>

By looking through the file structure we can see the flag inside mail-masta:
![image5](../../../../../_resources/image5-52.png)

HTB{3num3r4t10n_15_k3y}

**HOW WOULD I DO THIS WITHOUT NEEDING TO LOOK THROUGH FOLDERS**
