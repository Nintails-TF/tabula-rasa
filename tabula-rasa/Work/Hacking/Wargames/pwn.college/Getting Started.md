---
date created: Friday, January 3rd 2025, 4:14:59 pm
date modified: Friday, January 3rd 2025, 6:33:26 pm
---

# Getting Started:

## Setting Up SSH:

The interesting thing about ssh, is that even if the service restarts or shuts-down you can immediately reconnect to it, which I thought was kind of awesome.

```Bash
# Blank passphrase not recommended.
ssh-keygen -t rsa -b 4096 -f ~/.ssh/pwn.college-key -N 'cuteduck'
# Upload the public key to the website.
ssh-add ~/.ssh/pwn.college-key # removes the need for -i flag.
ssh hacker@pwn.college 
```

You can run challenges in **practice mode** which gives you access to `sudo`, which enables you to test things. 

It's important to remember:
1. *You can store files in your persistent home directory `aka /hacker`*
2. *You should either move to root or use `/./challenge/solve` if you want to solve a solution.
