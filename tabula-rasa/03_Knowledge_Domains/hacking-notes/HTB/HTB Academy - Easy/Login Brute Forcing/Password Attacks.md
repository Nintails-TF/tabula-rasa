---
title: 'Password Attacks:'
updated: 2023-08-13T20:29:16.0000000+01:00
created: 2023-08-13T20:00:49.0000000+01:00
---

Introduction:

When looking for viable targets to perform **log-in brute forcing** we want to look for web-servers that are running **Basic HTTP AUTH**. This is because it is easy to send requests to and get responses quickly.

The HTTP specification provides two authentication mechanisms:

1.  **Basic HTTP AUTH** is used to authenticate users to a HTTP server
2.  **Proxy server authentication** is used to authenticate a user to an intermediate proxy server.

Basic HTTP AUTH uses a username (user ID) and a password for authentication. The client first sends information without authentication information first - the servers response will contain **WWW-Authenticate** field in the HTTP header this then requests the client to provide credentials.

Once a request is sent, a character string will tell the client who is requesting the data - then this encoded data is transferred in the HTTP header **authorization field.**

The data is transferred in **base64** which is insecure.

Types of Brute Force attacks:

We have various methods of brute force attacks:

- **Dictionary attacks**
- **Brute forcing**
- **Traffic inspection**
- **MITM (Man-In-The-Middle) Attacks**
- **Key logging**
- **Social Engineering**
Brute Force Attacks:

A brute force attack tries all combinations of characters for a specified length, the issue with this is that **long and complex passwords** will take **years** to crack.

Even with a password length of 4 and only lowercase English letters, we would need to look at around **400,000 different passwords**.

So raw brute force attacks aren't that feasible. So we should increase the odds of guessing the correct password by using **dictionary attacks.**

Dictionary Attacks:

A **Dictionary Attack** is an attack that tries to guess passwords using the help of lists. We need to use wordlists in combination of brute forcing.

This leads to cracking the more common passwords much faster.

Methods of brute force attacks:

We have a few different ways to perform brute force attacks:

1.  Online Brute Force Attack
    1.  *Attacking a live app over HTTP, HTTPs, SSH, FTP, etc.*
2.  Offline Brute Force Attack
    1.  *Attacking an encrypted password hash*
3.  Reverse Brute Force Attack
    1.  *i.e. username brute-forcing - using a common password with a username list.*
4.  Hybrid Brute Force Attack
    1.  *Attacking a user using a customized wordlist - built on information gathered about the user.*

