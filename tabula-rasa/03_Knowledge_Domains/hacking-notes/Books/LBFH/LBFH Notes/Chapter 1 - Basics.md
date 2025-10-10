---
title: Chapter 1 - Basics
updated: 2023-01-30T09:16:22.0000000+00:00
created: 2022-07-28T17:39:55.0000000+01:00
date modified: Monday, May 20th 2024, 7:53:56 pm
---

Important Terms and Concepts:

**Binaries** - In terms of windows these refer to applications that can be executed (basically .exe files for Linux). These often are located in */usr/bin or usr/sbin* directory. Binaries such as ps, cat, ls and cd are common universal Linux commands and you also have Kali tools like aircrack-ng and intrusion detection systems (IDS) like Snort.

**Root** - This is the Linux superuser/admin account that allows the usage of nearly any command on the system, the holy grail of hacking is getting root control of a machine.

**Scripts** - These are series of commands that run in an interpretive environment that convert instructions into code. Many hacking tools are scripts - many *hackers* are simply script kiddies that run scripts of hacking tools to compromise and mess with systems - Scripts can be run via the bash interpreter or any other language like Perl, Ruby or Python. Python is one of the most popular languages for writing scripts in.

**Shell** - the shell is the environment and interpreter for running commands in Linux, The most widely used shell is bash (which stands for Bourne-again shell). Not to be confused with the **Terminal** which is the CLI of Linux.

The Terminal:

The terminal can be opened by clicking the terminal icon. The terminal is what runs the **shell** and enables users to run commands on the underlining OS and create scripts. Useful Shortcuts Include:

CTRL+ALT+T - Opens a Terminal
CTRL+SHIFT+X - Clears the active terminal.
CTRL+SHIFT+W - Closes the current terminal tab.
CTRL+SHIFT+T - Opens a new terminal tab.
CTRL+SHIFT+N - Opens a new terminal window. (Must be in terminal)

As a hacker, you will spend lots of time in the terminal, so learn important shortcuts, commands and make it comfy and easy to use.

Powerful Searches using find:

The **find** command is one of the strongest searching utilities. It can filter for many different parameters, the basic syntax is as followed:
![image1](../../../../_resources/image1-3.png)
So if you wanted to look for all files with the name apache2, you would use:
![image2](../../../../_resources/image2-2.png)
1.  Starting at the root of the file system
2.  Search for files
3.  Named apache2

This is slow, so we can make it faster by only searching in directories in which we expect to find the file:
![image3](../../../../_resources/image3-1.png)
This is much faster, since we only need to search the /etc/ directory.

**Importantly, find searches for EXACT matches.** If you want to search for anything that isn't just named "apache2" you need to use wildcards (\*):
![image4](../../../../_resources/image4.png)

This find command will:
1.  Search from the /etc/ directory
2.  For files
3.  That are named apache2, with **any** file extension.

Wildcards:
- \* searches for all characters of any length and size.
  - It is easily the most used wildcard.
- \[\] is used to match characters that appear inside the brackets.
  - \[c, b\]at would match **cat** and **bat** but not **hat** and **mat**.
- ? Is used to represent a single character.
  - ?at would match **cat, bat** but not **what.**
Linux Filesystem:

Linux is different than Windows in that it doesn't use physical drives, like C: and D:, but uses one logical filesystem, the base of the filesystem is /. Or often referred to as root (This is different from the root user or admin). The following diagram can illustrate the filesystem:

![image5](../../../../_resources/image5.png)

The key subdirectories are:

**/root -** The home directory of the root user.
**/etc -** Generally contains Linux config files, files that control how and when programs start up.
**/home -** The user's home directory.
**/mnt -** Where other systems are attached or mounted (hence the name mnt) to the filesystem.
**/media -** Where CDs and USB devices are attached or mounted to the file system.
**/bin -** Where application binaries are stored (the .exe files) reside.
**/lib -** Where libraries are stored (the equivalent of windows DLLs).

Basic Commands In Linux:
- *Using cd .. You can move up one level.*
  - *You can use cd .. .. To move up **two** levels.*
  - *Cd with no parameters can take you to root.*
- *Ls -l enables you to see more details about files. (long)*
  - *Ls -a enables you to see hidden files.*
- *To get help use -h, --help or man.*

Finding Stuff:

The easiest way to find files is using **locate.** What locate does it that it goes through your **whole filesystem** and checks for every occurrence of a keyword. It is very useful, but not perfect and has a few issues:

- Locate can give an overwhelming amount of files.
- Locate only updates its database once per day.
  - This means that newly created files aren't listed.

You can instead use **whereis** to locate binaries (executables). It also lists its source and manual page. Similar to whereis you can use **which**. This is an even more specific search that only returns binaries that are on **PATH**.

The PATH normally consists of binaries that are inside /**usr/bin** and may include **/usr/sbin/**.

Filtering with grep:

Very often we will want to search for a keyword, we can use **grep** to do this. We often using **command piping** to use grep. So if we want to list all processes we use **ps.** We can combine this with grep, to search for processes that are tunning that are **apache2**:
![image6](../../../../_resources/image6.png)

Modifying Files and directories:

You can create files in two ways: **touch** and **cat**.

1.  Using touch
    1.  Touch \[new file\]
        1.  It's simple as pie.
2.  Using cat.
    1.  You need to use a redirect symbol (\>) along with a file name:
        1.  ![image7](../../../../_resources/image7.png)
    2.  Then you'll be in **iterative mode** and you can type a message.
        1.  **To leave interactive mode, use CTRL + D**

**Appending to a file:**
