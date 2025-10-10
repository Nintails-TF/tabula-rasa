---
title: Nibbles - Metasploit
updated: 2022-12-21T16:55:07.0000000+00:00
created: 2022-12-21T13:17:18.0000000+00:00
---

The Metasploit method is a lot simpler, but there is less knowledge and experience you can gain from it.

1.  Start metaploit (*msfconsole)*
2.  Search for **nibbleblog** exploits
    1.  Use \[num\] to select the exploit
3.  Configure *rhosts* as the targets IP and *lhosts* as our VPNs IP
    1.  *Show options* shows other options.
4.  Set username to **admin** and password to **nibbles**
5.  Set target URI to **nibbleblog**
6.  Change the payload type to *generic/shell_reverse_tcp*
7.  Start the exploit.
8.  Follow step 4 and escalate out privileges to root.
