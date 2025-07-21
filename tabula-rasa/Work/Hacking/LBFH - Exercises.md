---
date created: Monday, December 30th 2024, 6:30:03 pm
date modified: Saturday, January 4th 2025, 10:56:53 am
---

# Chapter 1 - Getting Started with the Basics:

1. Use the `ls` command from the root (/) directory to explore the
directory structure of Linux. Move to each of the directories with
the `cd` command and run `pwd` to verify where you are in the directory
structure.
2. Use the `whoami` command to verify which user you are logged in as.
3. Use the locate command to find word lists that can be used for
password cracking.
4. Use the `cat` command to create a new file and then append to that
file. Keep in mind that > redirects input to a file and >> appends to a
file.
5. Create a new directory called hacker directory and create a new file in
that directory named hacked file. Now copy that file to your /root
directory and rename it secret file.

## Answers:

3. Using `find` or `locate` on the term *wordlists*, will give any wordlist within Kali.

This isn't a perfect method, since you get a ton of results that aren't related to password cracking.  But we can filter the search result to look for wordlists:

``` Bash
find -type d -name *wordlist* # Find any directory that has wordlist in it.
find 2>/dev/null -type d -name *wordlist* # Similar to first example, but supresses any error commands - mainly permission denied.
```

Completed all tasks, 1, 2, 4, 5 aren't that noteworthy in this case.

***

## Chapter 1 - Advanced Tasks:

File Permissions Challenge:
```Bash
- Create a directory called 'secure_docs'
- Inside it, create three files: 'public.txt', 'group_only.txt', and 'private.txt'
- Set permissions so that:
  * public.txt is readable by everyone (644)
  * group_only.txt is readable/writable only by owner and group (660)
  * private.txt is accessible only by the owner (600)
- Create a new user and group, then test if the permissions work as intended
- Use 'ls -l' to verify the permissions
```

This problem can be split into a few different parts:
- How do I change file permissions?
- How do I create a new user?
	- How do switch between users?
- How do I make a new group?
	- How do I add users to a group?

### Changing File Permissions:

Using either the [**numeric mode**](https://www.ibm.com/docs/en/aix/7.2?topic=modes-numeric-representation-access) or **[symbolic mode](https://www.ibm.com/docs/en/aix/7.2?topic=modes-symbolic-representation-access)** you modify file permissions.

```Bash
chmod 664 public.txt # Viewed by all
chmod 660 group_only.txt # Can be read and written to by owner + group
chmod 600 private.txt # Only can be read and written to by its owner.
```

[This page has a good display of how chmod permissions work.](https://chmodcommand.com)

Now the task involves creating a new user and group and switching between them.
```Bash
sudo groupadd developers # Will add a new group called developers.
sudo useradd username # Will add a new user.
sudo usermod -g groupname username # Will add a user to a group as primary group.
sudo passwd username # Sets the password for a user.
cat /etc/passwd | grep username # Check to see if the user has been added.
cat /etc/group | grep groupname # Check to see if the group has been added.
groups username # Checks the groups that a user is associated with.
```

We can associate our new group `spies` with the file `group_only.txt` using the command:
```Bash
sudo chgrp spies group_only.txt
```

We can switch users using `su` or `sudo`:
```Bash
su username # You'll then be prompted for a password
su # switches you to root, then you'll need to input the root password.
sudo -i -u username # Switches you to a user.
sudo -i # Switches you to root
exit # returns to the original user.
```

We can remove users and groups like so:
```Bash
sudo userdel username # Deletes user, but keeps files. Files will be orphaned.
sudo userdel -r username # Deleters user and home files.
sudo gpasswd -d username groupname # Kicks a member from a group.
sudo groupdel groupname # Deletes a group, note that group must have 0 members.
find / -uid old_UID # finds any orphaned files.
find / -uid old_UID -exec rm -rf {} \; # deletes orphaned fils.
```

With these commands, we can setup user accounts and group accounts:
![[Pasted image 20241231140130.png]]

After checking the unprivileged user bob and the group member jamesbond. The task is done and we can delete the unused groups and users.

***

### Advanced File Search and Manipulation:
```Bash
- Use 'find' to locate all .log files in /var/log that are larger than 1MB
- Create a new directory called 'large_logs'
- Use xargs with find to copy these files to your new directory
- Use 'grep' to search all copied logs for the word "ERROR" and redirect the output to 'error_summary.txt'
```

```Bash
find /var/log -size +1M # Would find any log file >1MB
mkdir large_logs
sudo find /var/log -size +1M | xargs cp -t filepath/large_logs # Copies any log file found to the large_logs folder.
```

The full command is complicated and requires some explanation:
``` Bash
find large_logs -type f -exec strings {} \; | sed 's/[^[:print:]\t]//g' | grep -i "ERROR" > error_summary.txt
```

1. We tell `find` to look inside `large_logs` and to look for files.
	1. For each file we find, we run strings on it to extract all printable characters.
		1. `{}` is a placeholder for the currently processed file.
		2. `\;` closes the `-exec` command.
2. Then `sed` is used to strip all non-printable characters (excluding tabs).
3. Finally we use `grep` to search for the word "ERROR" and to return lines that have it.
	1. the `-i` flag makes the search **case-insensitive** so "ERROR", "error", etc. are returned.
4. We create or overwrite the to the file of `error_summary.txt`

Now we have a error summary of all errors within our /var/logs in a human-readable format:
```Bash
...SNIP...
MESSAGE=[system] Rejected send message, 0 matched rules; type="method_return", sender=":1.347" (uid=1000 pid=1233 comm="/usr/bin/wireplumber") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.1" (uid=0 pid=799 comm="/usr/libexec/bluetooth/bluetoothd")
...SNIP...
```

***

## Archive Management:
```Bash
- Create a directory structure with at least 3 levels of subdirectories
- Place different types of files in each directory (.txt, .log, .conf)
- Create a tar archive of the entire structure while preserving permissions
- Create a compressed version using gzip
- Extract specific files from the compressed archive without extracting the whole thing
```

Creating a file structure with files is relatively trivial. But how do we make a tar archive that preserves the file structure and permissions? The flags of `-c`, `-p` and `-f` can be used to *create a new tar archive*, *preserve file permissions* and *state the name of the archive.*

```Bash
tar -cpf archive.tar dir_name # Creates a tarball with permssions intact.
man tar | grep "\-c" # Use to search manual for flags relating to -c.
gzip archive.tar # This will use gunzip to zip the tarball.
```

Of note, you need a backslash when grepping for any text starting with a hyphen. Since a `-` can be treated by a special character in regular expressions. 

Now that the archive is zipped up, we can figure out how navigate, search it and extract what we want from it.

```Bash
tar -tzf archive.tar.gz # We use -t to list the archive and -z to treat it as gzip, which is for compatability.
tar -xzf myArchive.tar.gz --strip-components=1 level1/options.conf
tar -xzf myArchive.tar.gz --strip-components=2 level1/level2/system.log
tar -xzf myArchive.tar.gz --strip-components=3 level1/level2/level3/note.txt
```

Thus we are able to extract all of the files we need without unzipping the whole archive.

### Improvements:

```Bash 
# 1. I could of made my filesystem quicker using:
mkdir -p dir_name/{level1,level2,level3} 
# 2. I could of used touch to create files like so, rather than cd'ing to them all.
touch dir_name/level1/options.conf 
touch dir_name/level2/system.log 
touch dir_name/level3/note.txt
```

***

## Symbolic Links and Hard Links:
```
- Create a directory called 'link_test'
- Inside it, create a file with some content
- Create both a symbolic link and a hard link to this file in different locations
- Move the original file and observe what happens to each link
- Use 'ls -li' to examine the inode numbers and verify the links
```

```Bash
# 1. Creating a dir called link_test
ln links-task/content/flippy-the-file.txt -t links-task/hard-link 
ln -s links-task/content/flippy-the-file.txt -t links-task/symbolic-link

# 2. Moving the text file.
mv links-task/content/flippy-the-file.txt /home/yangod/Projects/LBHF/Chapter-1

# 3. Checking on the hard and symbolic link
ls -la links-task/hard-link
ls -la links-task/symbolic-link

"""
We can see that the symbolic link is now broken whilst the hard-link still remains, now we can test to see if the links still work.
"""

# 4. Testing the links.
cat links-task/hard-link/flippy-the-file.txt
> Hi, my names flippy!
cat links-task/symbolic-link/flippy-the-file.txt
> cat: links-task/symbolic-link/flippy-the-file.txt: No such file or directory

"""
As we can see, we can still access the file using the hard link because it directly references the same location in data as "flippy-the-file.txt". Where as the symbolic link holds a pointer to the file, so if the file is moved the link breaks.
"""

5. Using 'ls li' to examine the link inode numbers.
# For the symbolic link, we can see where the dead link points to.
ls -li links-task/symbolic-link/flippy-the-file.txt
> 8674668 lrwxrwxrwx 1 yangod yangod 38 Jan  1 18:32 links-task/symbolic-link/flippy-the-file.txt -> links-task/content/flippy-the-file.txt

# For the hard link
ls -li links-task/hard-link/flippy-the-file.txt
> 8674624 -rw-r--r-- 2 yangod yangod 21 Jan  1 19:21 links-task/hard-link/flippy-the-file.txt

6. We can analyse the hard link by checking files that share the same inode
find /home/yangod/Projects/LBHF/Chapter-1 -inum 8674624
> /home/yangod/Projects/LBHF/Chapter-1/links-task/hard-link/flippy-the-file.txt
> /home/yangod/Projects/LBHF/Chapter-1/flippy-the-file.txt

"""
So now we know where the file has been moved to by looking at the inode number of the hard link and we could move it back to the /content dir if we wanted the sym link to work again.
"""
```

## Explaining Inodes through `ls -li`:

Example: `8674624 -rw-r--r-- 2 yangod yangod 21 Jan  1 19:21 links-task/hard-link/flippy-the-file.txt`

| **Field**        | **Example**                                | **Description**                                                                               |
| ---------------- | ------------------------------------------ | --------------------------------------------------------------------------------------------- |
| Inode Number     | `8674624`                                  | Unique identifier for the file in the file-system. Shared by all hard links to the same file. |
| File Permissions | `-rw-r--r--`                               | Indicates file type and permissions: owner (`rw`), group (`r`), others (`r`).                 |
| Link Count       | `2`                                        | Number of hard links pointing to this file. Indicates how many filenames reference the inode. |
| Owner            | `yangod`                                   | The username of the file's owner.                                                             |
| Group            | `yangod`                                   | The group associated with the file.                                                           |
| File Size        | `21`                                       | Size of the file in bytes.                                                                    |
| Last Modified    | `Jan 1 19:21`                              | Date and time of the file's last modification.                                                |
| File Path        | `links-task/hard-link/flippy-the-file.txt` | The relative or absolute path to the file.                                                    |

**Completion Time:**
*247 Minutes for Chapter 1 tasks*
*9.88 Pomodoro cycles*

***

# Chapter 2 - Text Manipulation:

## Basic Tasks:

1. Navigate to /usr/share/wordlists/metasploit. This is a directory of multiple
wordlists that can be used to brute force passwords in various password-
protected devices using Metasploit, the most popular pentesting and
hacking framework.
2. Use the `cat` command to view the contents of the file passwords.lst.
3. Use the `more` command to display the file passwords.lst.
4. Use the `less` command to view the file passwords.lst.
5. Now use the `nl` command to place line numbers on the passwords in
passwords.lst. There should be 88,396 passwords.
6. Use the `tail` command to see the last 20 passwords in passwords.lst.
7. Use the `cat` command to display passwords.lst and pipe it to find all the
passwords that contain 123.

**All basic tasks are trivial.**

# Advanced Tasks:

## Counting Frequency for Special Character Passwords:
```
Search through passwords.lst for entries containing special characters (!@#$%^&*), count how many occurrences of each special character exist, and sort them by frequency. Use a combination of grep, sed, sort, and uniq commands.
```

**Questions:**
1. How do we filter for special characters?
2. How do we count occurrences of special characters?
3. How do we sort by frequency?

```Bash
1. "Use a negated regular expression:"
grep '[^a-zA-Z0-9]' file.txt # ^ means not listed in brackets and a-zA-Z0-9 covers all alphanumeric characters.
2. "We count occurrences using uniq:"
uniq -c # Counts each ocurence of that character
3. "We use sort:"
sort -nr # Sorts numerically in reverse, highest number at top of file.
```

Combining this all gives us:
```Bash
cat password.lst | grep -o [^a-zA-Z0-9] | sort | uniq -c | sort -nr
```

***

## Password Length Checker:
```
Create a new file that contains only passwords between 8-12 characters long from passwords.lst, then find all entries that have both letters and numbers but no special characters. Use wc, grep with regex, and output redirection.
```

**Questions:**
1. How can we filter for words of a specific length?
	1. Using regular expressions within -P for Pearl regex.

```Bash
 # We can reverse our previous search, to only get alphanumeric characters.
grep -v '[^a-zA-Z0-9]' password.lst
# The final command
grep -P '^[a-zA-Z0-9]{8,12}$' password.lst > /home/yangod/Projects/LBHF/Chapter-2/password8-12length.txt
```

***

## Password Comparison:
```
- Compare passwords.lst with another wordlist (like rockyou.txt), find common passwords between them, and output only those that appear in both files.
```

**Question:**
- How do we use `comm` to compare two files?
- How can we find and decompress rockyou?
	- Using `locate` we can find rockyou.

```Bash
gunzip rockyou.txt.gz # Decompresses rockyou.
comm -12 <(sort /usr/share/wordlists/metasploit/password.lst) <(sort /usr/share/wordlists/rockyou.txt)
```

This code requires some explanation:
- `comm -12`
	- This will suppress output from files 1 and 2 and only show `-3` which is that lines that match in both files.
- `<(sort file.txt)`
	- This sorts the password files on the fly using substitution, so that the original files aren't modified.

We then are able to cat the matching passwords to file.

***

## Sequential Passwords:

```
- Find all sequential number patterns (like '123', '234', '345', etc.) in passwords.lst, extract them into their own file, then count how many times each sequence appears. Sort results by frequency. Use grep with regex patterns, sort, uniq, and awk.
```

I'm not exactly sure how to search for sequential patterns, but this would be my best guess.

```Bash
"""
This task is MUCH harder than the rest and really goes into a more advanced areas of text manipulation.
"""

# Cringe chatGPT solution... must fix at some point.
awk '/^[0-9]+$/ {         
    seq = 1
    for (i = 2; i <= length($0); i++) {
        if (substr($0, i, 1) != substr($0, i-1, 1) + 1) {
            seq = 0
            break
        }
    }
    if (seq) print $0
}' password.lst | sort | uniq -c | sort -nr > /home/yangod/Projects/LBHF/Chapter-2/seqPasswords.txt
```

**Completion Time:**
*100 Minutes for chapter 2 tasks*
*4 Pomodoro cycles*

***
