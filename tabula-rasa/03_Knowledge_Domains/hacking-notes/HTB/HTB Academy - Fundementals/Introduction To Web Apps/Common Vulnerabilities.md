---
title: 'Common Vulnerabilities:'
updated: 2023-07-18T20:52:59.0000000+01:00
created: 2023-07-18T16:56:10.0000000+01:00
---

Broken Auth/Access Control:

**Broken authentication** and **Broken Access Control** is the top of the OWASP top 10 and is a reoccurring and dangerous vulnerability for lots of web applications.

**Broken Authentication** refers to vulnerabilities that enable attackers to bypass authentication functions. For example, subverting login pages, escalating privileges from a normal user to an admin.

**Broken Access Control** refers to vulnerabilities that enable attackers to access sensitive pages and features they shouldn't normally have access to, like attackers gaining control of an admin panel.

*For example, College Management System 1.2 has a simple [Auth Bypass](https://www.exploit-db.com/exploits/47388) vulnerability that allows us to login without having an account, by inputting the following for the email field: ' or 0=0 \#, and using any password with it.*

Malicious File Upload:

Another critical issue is via uploading malcious scripts and payloads. If a website has an upload feature we can try and upload malicious scripts (i.e. a PHP reverse shell) which could allow us to execute commands on the remote server.

Even though this is basic, many developers are not aware of these threats so they do not design their code to check uploaded files integrity. Developers who do put checks in can also be bypassed. Which still allows threat actors to upload malicious scripts.

*For example, the WordPress Plugin Responsive Thumbnail Slider 1.0 can be exploited to upload any arbitrary file, including malicious scripts, by uploading a file with a double extension (i.e. shell.php.jpg). There's even a [Metasploit Module](https://www.rapid7.com/db/modules/exploit/multi/http/wp_responsive_thumbnail_slider_upload/) that allows us to exploit this vulnerability easily.*
Command Injection:

Many web applications require OS commands to perform certain processes - for example a web app may need to install a python library of our choosing by trying to execute an OS command that requires said library.

This is dangerous because if not properly filtered, an attacker can inject other OS commands which could allow them to get a foothold on the system and gain control of the back-end.

This is widespread, since developers either have no sanitization or weak tests that can be bypassed.

*For example, the WordPress Plugin Plainview Activity Monitor 20161228 has a [vulnerability](https://www.exploit-db.com/exploits/45274) that allows attackers to inject their command in the ip value, by simply adding \| COMMAND... after the ip value.*

SQL Injection (SQLi):

**SQL Injection** is also a very common vulnerability. This occurs when a web application executes a SQL query that is supplied from a user - but is not filtered correctly. This enables us to take over control of the database and the hosting server.

*For example, the same previous College Management System 1.2 suffers from a SQL injection [vulnerability](https://www.exploit-db.com/exploits/47388), in which we can execute another SQL query that always returns true, meaning we successfully authenticated, which allows us to log in to the application. We can use the same vulnerability to retrieve data from the database or even gain control over the hosting server.*
