---
title: 'Default Passwords:'
updated: 2023-08-16T11:27:14.0000000+01:00
created: 2023-08-13T20:29:42.0000000+01:00
---

Introduction:

Default passwords are frequently used with user accounts for testing purposes. They are often easy to remember and are used for default accounts for services and applications to make access easier.

*It is not uncommon for developers to forget about the existence of these user accounts - which we can potentially exploit.*

When we perform the **Basic HTTP Authentication** form to enter a username and password we frequently receive a **401 Unauthorized** response code. We can use brute-force attacks, when we lack the information to structure a better attack.

Hydra:

**Hydra** is a great tool for brute forcing logins, as it can be used in a wide range of attacks and services and it is faster than other password brute-forcing tools.

**Apt install hydra** will enable us to install it. We can use the -h flag to get details on how to use the tool.

Default Passwords:

As we don't have a username, we need to brute force both fields, we can use wordlists for usernames or we can brute force both fields - generally this is a last resort as brute forcing two fields is very fucking slow.

We can use our friend **SecLists,** and look at the **default credentials** to test various common user/password combos.

It is very common for admins to overlook test accounts and their credentials, We can even test the top 3-5 cred combos manually.

Activity:
![image1](../../../../_resources/image1-181.png)

1.  Using Hydra, we should use the combined cred wordlists
    1.  Ftp-betterdefaultpasslist.txt from seclists.
2.  After that we need to define the port and request method
    1.  **-C** for our cred list
    2.  **-s** to define port
    3.  Http-get is our request method
3.  Finally, we define the target path - in this case root.
    1.  Simply /
![image2](../../../../_resources/image2-149.png)

Output:
![image3](../../../../_resources/image3-115.png)

