---
title: Value Fuzzing
updated: 2023-07-30T22:12:07.0000000+01:00
created: 2023-07-30T16:53:55.0000000+01:00
date modified: Monday, May 13th 2024, 10:54:48 pm
---

Introduction:

Now that we have a working parameter (user) that we can use to return the flag content we want, we now need to fuzz for the parameter values - to do this we need to make our **own wordlist**.

Custom Wordlists:

When we try and fuzz parameters we may not always have a pre-written wordlist. The steps we should take here are:

1.  Look for wordlists in **seclists.**
2.  Guess the structure of the parameter using context.
    1.  e.g. we have the parameter **id** so we can guess that they use numbers, either in a custom format or sequentially.
3.  We can make a wordlist that has all numbers between 1-1000, etc.

We can do this quickly via **bash scripting:**
![image1](../../../../_resources/image1-147.png)

Fuzzing with our custom wordlist:
ffuf -w ids.txt:FUZZ -u [http://admin.academy.htb:PORT/admin/admin.php](http://admin.academy.htb:PORT/admin/admin.php) -X POST -d 'id=FUZZ'-H 'Content-Type: application/x-www-form-urlencoded'-fs xxx

Example Fuzzing:
![image2](../../../../_resources/image2-119.png)

*We can see that using the id of 73 returns a valid response.*

*Performing a curl search on the website reveals the flag:*
![image3](../../../../_resources/image3-92.png)

***We could also do this in BURP if we wanted to see the regular site content.***
HTB{p4r4m373r_fuzz1n6_15_k3y!}
