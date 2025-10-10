---
title: 'Privilege Escalation:'
updated: 2022-10-23T20:19:16.0000000+01:00
created: 2022-10-18T14:51:03.0000000+01:00
---

Scheduled Tasks:

Both in Linux and Windows systems there are scripts that run at specific intervals - like anti-virus scans. We can take advantage of these system via **cron jobs** (Linux) or **scheduled tasks** (Windows). We do this via:

- Adding new scheduled tasks
- Tricking scheduled tasks in running malicious code.

The simplest way of doing these things is to check if we can add new scheduled tasks. We can do this in Linux via **Cron Jobs.** There are specific directories that we can use to add new cron jobs if we have write permissions. They are:

1.  /etc/crontab
2.  /etc/cron.d
3.  /var/spool/cron/crontabs/root

If we are able to write to a directory that gets called by a cron job, then we can write a bash script that has a reverse shell command, then when a cron job gets executed we can execute a reverse shell.

Exposed Credentials:

The best place to try and locate creds is inside **log** and **configuration** files along with **user history** files. Tools like PEASS often look for potential passwords for us.

You may also be able to reuse passwords, if the same password is used for databases, then maybe the users account also has the same password or ssh has the same password.

SSH keys:
Finally, if we have read access over .ssh for a specific user, we can read their ssh key found in /home/user/.ssh/id_rsa or /root/.ssh/id_rsa, then use it to login as them:

![image1](../../../../_resources/image1-77.png)

Furthermore; if we have write access to a user's /.ssh/ directory we can place our public key in there user's SSH directory at */home/user/.ssh/authorized_keys.* This allows us to gain ssh access after gaining shell on that user.

First we need to create a new key using ssh-keygen:
![image2](../../../../_resources/image2-59.png)

From this we get 2 files: key and key.pub

We use the key with our ssh on our remote machine and we copy key.pub to the remote machine.
![image3](../../../../_resources/image3-51.png)

Then we use the key file when connecting using ssh:
![image4](../../../../_resources/image4-42.png)
Once we gain access into a system, we are usually a low-privileged normal user. Which does not give us complete control over the system. To gain full access we need to exploit a vulnerability that would execute us to a root or admin level user. So how do we do this?

PrivEsc Checklists:

Once we gain access to a box we want to enumerate everything to check for anything vulnerable. We can use checklists and cheat sheet that provide us with a checklist of commands to run and things to check. Resources include:

- [HatTricks](https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-methodology) (Includes other pen testing methodologies)
- [PayloadAllTheThings](https://swisskyrepo.github.io/PayloadsAllTheThingsWeb/#documentation)

Starting to use and experiment with various commands and techniques is a good way to get familiar and understand weaknesses that can lead to raising our privileges.

Enumeration Scripts:

We can use automated scripts to quickly look for any vulnerabilities. Examples of these tools include:

Linux:
- [LinEnum](https://github.com/rebootuser/LinEnum)
- [linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker)
Windows:
- [Seatbelt](https://github.com/GhostPack/Seatbelt)
- [JAWS](https://github.com/411Hall/JAWS)

By in large the most popular tool for enumeration is [PEASS](https://github.com/carlospolop/PEASS-ng) which is well maintained and can be used on Windows **and** Linux.

**DO NOTE**: These automated scripts can trigger anti-virus software or security monitoring software (SIEM). This can prevent the script from running or alert security that a system has been compromised. Sometimes the better way of enumeration is to manually enter commands.

Kernel Exploits:

We should check and note the version of the system or computer we are in, as older/legacy servers may not be maintained with updates and patches, making them vulnerable to exploit.

We can then use **searchsploit** or google for and vulnerabilities for the version of OS that is running. For example: Linux version 3.9.0-73-generic is vulnerable to CVE-2016-5195 (DirtyCow). We can download this exploit then run it on the server to gain access.

Note that kernel exploits often have the downside that they case system instability and we need to be careful before running them on production machines. It's good practice to run them in a lab first.

Vulnerable Software:

Another method of gaining privileges would be exploiting programs that are running on the machine, we should look for exploits are on any software, especially older versions of software.

In Linux we can do this using: **dpkg -l**
On windows, we would look inside program files.

User Privileges:

We should test our level of privileges on the current user we are on and check for privileged users or root. There a three main ways of doing this:

1.  Sudo
2.  SUID
3.  Windows Token Privileges.

The way we do this in Linux is that:

1.  We check using **sudo -l** what privilages we have
2.  Try use **sudo su -** to get complete access to the system.
    1.  This allows us to execute all commands without needing to provide a password.
3.  We can look inside **sudo -l** to see if there is any location that lets us use sudo commands.
4.  We can try to exploit locations to try get a shell.
    1.  Linux we use: [GTFOBins](https://gtfobins.github.io/)
    2.  Windows we use: [LOLBAS](https://lolbas-project.github.io/)

