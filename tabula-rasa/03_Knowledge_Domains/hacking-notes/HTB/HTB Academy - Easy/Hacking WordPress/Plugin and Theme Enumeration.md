---
title: 'Plugin and Theme Enumeration:'
updated: 2023-07-19T20:49:14.0000000+01:00
created: 2023-07-19T18:20:09.0000000+01:00
---

Similarly to looking at core WP version we can inspect the source code or we can use the grep method.

Viewing source code:

We can filter for **plugins** and look for wp plugins:
![image1](../../../../_resources/image1-124.png)

Viewing using grep:

Using grep, [sed](https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/) (stream editor) and cut we can filter for Wordpress themes and plugins:

**WordPress Plugins:**
curl-s -X GET <http://blog.inlanefreight.com> \|sed 's/href=/\n/g' \|sed 's/src=/\n/g' \| grep'wp-content/plugins/\*' \| cut-d"'"-f2
![image2](../../../../_resources/image2-100.png)

**Wordpress Themes:**
curl-s -X GET <http://blog.inlanefreight.com> \|sed 's/href=/\n/g' \| sed's/src=/\n/g' \| grep'themes' \| cut-d"'"-f2
![image3](../../../../_resources/image3-80.png)

The response headers may also contain version numbers for specific plugins.

*The problem is that not all installed plugins and themes can be discovered passively. In this case, we need to perform active enumeration. We do this by sending **GET requests** that points to a directory or file that may exist on the server.*

*If the directory or file does exist, we can gain access to the directory or file or we can get a redirect response, indicating that the content response does exist. But we do not have access to it.*

Plugins Active Enumeration:

So if we try and access the **mail-masta** plugin:

curl-I -X GET <http://blog.inlanefreight.com/wp-content/plugins/mail-masta>
![image4](../../../../_resources/image4-65.png)

If the content does not exist, we will get a **404 not found error:**

curl-I -X GET <http://blog.inlanefreight.com/wp-content/plugins/someplugin>
![image5](../../../../_resources/image5-51.png)

We can speed up enumeration, we can write a bash script or use a tool such as **wFuzz** or **WPScan**.

