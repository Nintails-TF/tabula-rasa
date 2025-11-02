---
date created: Tuesday, December 31st 2024, 9:58:25 am
date modified: Friday, January 3rd 2025, 11:11:10 am
---

# Linux Basics For Hackers Summaries:

# Introduction Summary:
- Hacking is a valuable and powerful skill to master, that will only see growth in the future.
- If you practice a few core areas of computing science knowledge, you will have a strong foundation to pursue other areas.
	- The hot flashy concepts like IoT or AI sometimes aren't the most important things to understand, but it doesn't hurt to know them either.
	- The core concepts are:
		1. Networking Fundamentals
		2. Programming and Scripting
		3. System architecture and administration
		4. Cryptography and security concepts
		5. Security testing methodology
		6. Web security
- The book is structured into a few main components
	- Chapters 1, 2, 4, 5, 6, 7, 9, 10, 11, 15 and 16 discuss features about Linux and how we can better use and manipulate the system we have.
	- Chapters 3, 13, 14 discuss using networks within Linux
	- Chapters 8 and 17 give an introduction to scripting.
	- Chapters 12 and 13 give an overview of some useful external tools.
- The majority of the book is about actually using and understanding a bit more about Linux, with some spice thrown in occasionally.

# Chapter 1 - Getting Started with Basics:

### Core Concepts:
- **Shell**: The command interpreter environment, with Bash being the most common.
- **Terminal**: The CLI interface used to enter commands.
- **Root**: The superuser account with full system privileges (use with caution).
- **Binaries**: Executable programs stored in /usr/bin and /usr/sbin.
- **Scripts**: Series of commands that can be interpreted and run by the system.

### Essential Commands
1. **Navigation**:
    - `pwd`: Show current directory
    - `cd directory`: Change directory
    - `ls`: List files (`-l` for details, `-a` for hidden files)
2. **File Operations**:
    - `touch filename`: Create empty file
    - `cat > filename`: Write to a file. 
	    - Use CTRL+D to exit interactive mode.
    - `cat >> filename` Append to a file. 
	    - Use CTRL+D to exit interactive mode.
    - `mkdir directory`: Create directory
    - `cp source destination`: Copy files
    - `mv oldname newname`: Move or rename
    - `rm filename`: Delete file (`-r` for directories)
3. **Search Tools**:
    - `find directory -type f -name pattern`: Search for files
    - `grep pattern`: Filter output for specific text
    - Wildcards: `*` (any characters), `?` (single character), `[ ]` (character list)

## Additional Commands:

1. [[LBFH/LBFH - Exercises#Changing File Permissions]]
	- `chmod`: Used to change file permissions
		- You can use [numeric mode](https://chmodcommand.com) or symbolic mode to change permissions
	- `groupadd`,`useradd`, `usermod`,`chgrp`,`su`,`userdel`,`groupdel` are used to manage new users and groups.
2. [[LBFH/LBFH - Exercises#Advanced File Search and Manipulation]]
	- Using `find` in combination with filtering to search and manipulate log files.
	- `strings` - Used to extract printable characters from a file.
	- `sed` - Used to perform text transformation from an input stream.
		- In our case `STDOUT`
	- `grep` - Used in searching for lines with specific text.
3. [[LBFH/LBFH - Exercises#Archive Management]]
	- `tar` used to create tarballs.
	- `gzip` used to compress files.
4. [[LBFH/LBFH - Exercises#Symbolic Links and Hard Links]]
	- `ln` Used to create symbolic and hard links
	- `ls -li` used to list inode information for files.
	- `find -inum` used to search for files with the same inode.

***

# Chapter 2 - Text Manipulation:

### Core Concepts:
1. In Linux everything is a file, so being able to manipulate text which is what files are made of is key.
	1. Important use-cases are: configuring applications, searching logs and filtering data.
2. Snort is a popular IDS.

### Essential Commands:

**File Viewing:**
- `cat`: Displays entire file content
- `head -n`: Shows first n lines
- `tail -n`: Shows last n lines
- `nl`: Numbers lines in file
- `more`: Views file page by page
- `ls -lh`: Shows size in human readable format.
- `less`: Interactive file viewer with search capabilities
    - Use `/` to search
    - `n` for next match, `N` for previous
    - `less -i` for case-insensitive search, or `I` when during runtime.

**Text Processing:**
- `grep`: Searches for patterns
    - `-A n`: Shows n lines after match
    - `-B n`: Shows n lines before match
    - `-v`: Reverses the result of a search
    - `-P`: Uses Perl regular expressions, used in more advanced `greps`
	    - `grep -P '^.{8,12}$' password.lst` - Filter for any password between 8-12 characters.
- `sed`: Stream editor for text transformation
    - `s/old/new/g`: Global replacement
    - `s/old/new/n`: Replace nth occurrence

**Redirection:**
- `>`: Redirects output to new file
- `|`: Pipes output between commands

### Additional Commands:

[[LBFH/LBFH - Exercises#Chapter 2 - Text Manipulation]]
- `uniq`: Used to report or omit repeated lines.
	- `-c` Used to count **unique** occurrences, by prefixing lines with the number of occurrences.
- `wc`: used to count the number of bytes/chars/lines
	- `-c` Used to count the lines in a file.
- `sort` : Used to sort and change the order of text.
	- `-n` sorts numerically.
	- `-r` sorts in reverse.
- `awk`: a UNIX programming language used for text programming has a similar function to`sed` and `grep`
- `comm` : compare two sorted files line by line.
	- `-12` Will only show lines that match in both files.
	- `comm` needs both files to be sorted before they are compared.
		- `<(sort file)` can be used on the fly if needed.
- `tr` : translate or delete characters

*** 
