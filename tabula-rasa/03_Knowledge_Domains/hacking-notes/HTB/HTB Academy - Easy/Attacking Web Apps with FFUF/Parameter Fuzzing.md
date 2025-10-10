---
title: 'Parameter Fuzzing:'
updated: 2023-07-30T16:41:56.0000000+01:00
created: 2023-07-25T15:21:24.0000000+01:00
---

Introduction:

If we run a recursive ffuf scan on the **admin.academy.htb** we find an admin.php page, which we do not have access to read:
![image1](../../../../_resources/image1-146.png)

This indicates that there must be some kind of **user identification.** We didn't login nor do we have any **cookie** information that can be verified at the backend. *So there may be a key that we can pass to the page to read the **flag.** Such keys are normally passed as a **parameter.***

We do this via **GET** and **POST** HTTP request. So how do we fuzz these?

(Fuzzing parameters may expose unpublished parameters that are publicly accessible. Such a parameters tends to be less tested and less secure, so it is important to test such parameters.)

GET Request Fuzzing:

Similarly to how we fuzz website pages, we can use ffuf to enumerate parameters. We can start fuzzing using GET requests which we can pass using the **?** Symbol, like so:

[***http://admin.academy.htb:PORT/admin/admin.php?param1=key***](http://admin.academy.htb:PORT/admin/admin.php?param1=key)

All we have to do is:

1.  Replace **param1** with the **FUZZ** keyword.
2.  Pick an appropriate wordlist
    1.  We can use the **SecLists** wordlist called **burp-parameter-names.txt**

ffuf -w /opt/useful/SecLists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u [http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key](http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key) -fs xxx

We do get a hit back but the method is deprecated.
Fuzzing Example:
![image2](../../../../_resources/image2-118.png)

The reason why we need -fs 798 is because we filter for size to avoid duplicate responses. *So we know that the **user parameter is accepted.***

