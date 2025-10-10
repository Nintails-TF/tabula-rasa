---
title: 'Level 0:'
updated: 2022-07-20T16:47:43.0000000+01:00
created: 2022-07-20T16:10:25.0000000+01:00
---

![image1](../../../_resources/image1-210.png)

So we need to learn how to connect to a server using SSH, that is the goal of this level.

This command works:

![image2](../../../_resources/image2-176.png)

(ssh username@remote, then use -p to specify the port)

Useful tools:

![image3](../../../_resources/image3-139.png)

What is SSH?:

SSH stands for Secure Shell Protocol and it is a cryptographic network protocol used to operate network services securely over an unsecured network. It is mostly used for remote login and command line execution.

SSH operates using a client-server architecture, in which a SSH client (your pc) connects to a instance of an SSH server (OTW bandit server). There are three main components of SSH.

1.  **Transport Layer -** provides server authentication, confidentiality and integrity
2.  **User Authentication Protocol -** validates the user to the server
3.  **Connection Protocol -** multiplexes the encrypted tunnel into multiple logical communication channels.

Open SSH made in 1999 and maintained by the open-source OpenBSD devs is a very popular software stack for SSH.

OpenSSH is what is used within Kali Linux.
