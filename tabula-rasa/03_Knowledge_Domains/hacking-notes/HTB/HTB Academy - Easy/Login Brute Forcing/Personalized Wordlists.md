---
title: 'Personalized Wordlists:'
updated: 2023-08-16T17:04:38.0000000+01:00
created: 2023-08-16T14:41:04.0000000+01:00
---

Password Policy:

Now that we have a wordlist, we can filter out passwords that we know aren't possible, for example:

1.  Passwords must be \> 8 characters
2.  Passwords must contain a special character
3.  Passwords must contain numbers

So we can remove passwords from our list that don't abide by these rules, **Hashcat** and **John** can use these as rules, but for **hydra** we will need to modify our wordlist like so:

![image1](../../../../_resources/image1-186.png)

Mangling:

We can use this personalized wordlist to create different **permutations** of the passwords, since we don't know if the user has added a number to the start or the end of their password.

Note that mangling should only be done when normal brute forcing fails and we can use tools like **rsmangler and The Mentalist**.

Since is because mangling wordlists will make them larger and take more time to work through.

Custom Username Wordlist:

We can also consider username wordlists, since we don't know if the username could be **b.gates, gates or bill**. The most basic method is just typing usernames in.
![image2](../../../../_resources/image2-153.png)

We can alternatively use **Username Anarchy**, to generate a wordlist of usernames. We can use it simply like:
![image3](../../../../_resources/image3-118.png)

Introduction:

To create a personalised wordlist for a user - we need to get details about them - if they are well known we can look them up on website like Wikipedia or we can perform basic google searches. A good module to learn about this is (<https://academy.hackthebox.com/module/details/20>).

CUPP:

We have many tools that can create custom wordlists, in this example we can use CUPP. In which after we run it in interactive mode using the -I flag. We insert info based on the target:
![image4](../../../../_resources/image4-94.png)
*(We can install cupp using apt install cupp).*

We will then receive a wordlist called **william.txt**

