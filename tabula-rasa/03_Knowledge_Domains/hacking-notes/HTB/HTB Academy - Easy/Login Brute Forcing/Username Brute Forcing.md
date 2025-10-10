---
title: 'Username Brute Forcing:'
updated: 2023-08-16T11:30:46.0000000+01:00
created: 2023-08-15T22:01:56.0000000+01:00
---

Activity:
![image1](../../../../_resources/image1-182.png)
In this example we need to brute force using the **amormio** password on a list of usernames:

hydra -L /usr/share/seclists/Usernames/Names/names.txt -p admin -u -f 94.237.62.195 -s 34152 http-get /

Remember that:
- -L
  - Defines the list of usernames we are trying
- -p
  - Defines the password we want to brute force
- -u
  - Means that we try all usernames on a single pw, instead of all pws on a single user
- -f
  - Stop on successful login
- -s
  - Our servers port number

Introduction:

One of the most commonly used password lists is **rockyou.txt** since it has **14 million** unique passwords which are sorted by how common they are and was leaked from an online database of passwords and usernames - unless a password is fully unique, rockyou will contain it.

For usernames, we can use **names.txt** as a quick list of common usernames.

Username and Password Attacks:

**Hydra** requires at minimum 3 flags to perform a brute force attack against a web service:

1.  **Credentials**
2.  **Target Host**
3.  **Target Path**

We can also separate credentials into **usernames** (-L) and **passwords** (-P). Since we don't care about brute forcing all usernames, we can force **hydra** to stop on the first **successful login using the -f flag.**

We can also use the -u flag to make sure that *all users are tried on a single password* instead of 14 million passwords being fuzzed for a single user.

***However, this is very slow because we need to go through two wordlists**.*

Username Brute Force:

If we only brute force the username, we can assign a static **username or password**, e.g. we can assign the username **test** by using *-l test* and adding the rockyou password list.

If we find a password that works, we can use **-p** to brute force any usernames that may have this password.

