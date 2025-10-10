---
title: Level 18 - Level 19
updated: 2022-10-20T15:55:12.0000000+01:00
created: 2022-10-20T15:51:58.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:07:58 pm
---

The password for level 19 is stored in a readme at the home directory, but you get logged out instantly when you try to log in using ssh.

This is because your .bashrc has been modified. It runs whenever bash is started, we can stop it using:

Bash -c exit;
