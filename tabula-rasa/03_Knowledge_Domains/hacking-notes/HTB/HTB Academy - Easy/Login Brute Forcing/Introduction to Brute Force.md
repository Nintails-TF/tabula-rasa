---
title: 'Introduction to Brute Force:'
updated: 2023-08-13T20:00:43.0000000+01:00
created: 2023-08-13T19:46:26.0000000+01:00
---

Introduction:

A brute force attack is a method of guessing passwords or credentials by automatic probing. Passwords are usually stored in hashes, so we perform **password cracking** to try get the cleartext password. Common locations on system for hashed passwords are:

- **Windows**
  - *Unattend.xml*
  - *Sysprep.inf*
  - *SAM*
- **Linux**
  - *Shadow*
  - *Shadow.bak*
  - *Password*

Since passwords cannot be calculated backwards from a hashed version, the brute force method figures out the hash values of random passwords until a hash value matches the stored hash. This is **offline brute forcing** - in which we are checking if two strings match each other.

We will be exploring **online brute-forcing** since there is almost always a method for admins, authors and users to login to a web application. Usernames are often recognisable or can be deduced and **complex passwords** are hard to remember.

This means that online brute forcing can prove to be a valuable technique if we cannot get an initial foothold.

Tools:

We can use various tools for **login brute-forcing**, such as:

- **Ncrack**
- **Wfuzz**
- **Medusa**
- **Patator**
- **Hydra**

Hydra is one of the more common and reliable tools for login brute forcing.

