---
title: Oopsie
updated: 2023-02-04T12:46:31.0000000+00:00
created: 2022-12-31T17:52:48.0000000+00:00
date modified: Monday, May 13th 2024, 10:21:30 pm
---

Enumeration:
Using Nmap reveals:

Using GoBuster, we can scan for common sub-directories, this reveals:
![image1](../../../../../_resources/image1-62.png)
![image2](../../../../../_resources/image2-47.png)

We can see that locations such as uploads exist, but we can't access them (301 - Forbidden).

Tip - **Spider the site with burp.**

*Looking at the Target tab, We can see all of the sub-domains within Burp:*
![image3](../../../../../_resources/image3-40.png)
*(cdn-cgi/login looks promising).*

We can use the link: <http://10.129.124.44/cdn-cgi/login/>. Which takes us to a login page:
![image4](../../../../../_resources/image4-32.png)

Going through as a guest allows us to access everything but **uploads.**

Lateral Movement:

Now that we have a reverse shell on the user **www-data.** We should take a look around, we can use **grep** to look for anything interesting - such as PHP and SQL files that we can enumerate further.

Firstly, we can **upgrade** our reverse shell to make it nicer to use:
![image5](../../../../../_resources/image5-22.png)

We should try look for anything that has a **password** or is a **php** file.

First we can look at /etc/passwd, which has a ton of creds, but doesn't really help us. Then we can use **find**, which shows us a ton of folders we don't have access to.

**Looking inside** /var/www/html/cdn-cgi/login/ **we can use grep to find a password:**
![image6](../../../../../_resources/image6-14.png)

if(\$\_POST\["username"\]==="admin" && \$\_POST\["password"\]==="MEGACORP_4dm1n!!")
\<input type="password" name="password" placeholder="Password" /\>

*We can search for all files ending in PHP whilst silencing error messages, using:*
**find / -type f -name \*.php 2\>/dev/null**
![image7](../../../../../_resources/image7-11.png)

Searching through these php files we come to **db.php:**
![image8](../../../../../_resources/image8-9.png)
mysqli_connect('localhost','robert','M3g4C0rpUs3r!','garage');

We can now log in as Robert using the **su** command:

![image9](../../../../../_resources/image9-8.png)

Abusing SUID:

What is SUID?:

*Set Owner User ID (SUID) has a special permission for the user access level and has a single function. A file with SUID enabled always executes as the user who owns the file, regardless of who is executing the command.*

*If the file owner doesn't have permissions, then an uppercase S can be used.*

*In our case **Bugtracker** is owned by root and we can execute it as root since it has SUID.*

This means that if we can muck around with **bugtracker** to get it to run the code we want, we can possibly get root!

Normally running **bugtracker** gives:
![image10](../../../../../_resources/image10-6.png)

The tool accepts user input, if we can get it to execute a shell, then we can get root!

1.  Navigate to /tmp/ and create a file named cat.
    1.  Make sure it is executable (chmod +x).
2.  We can exploit bugtracker by adding /tmp/ to the PATH environment
    1.  Export PATH=/tmp:\$PATH
3.  Check our path
    1.  Echo \$PATH
4.  THEN execute bugtracker from /tmp/

![image11](../../../../../_resources/image11-5.png)

![image12](../../../../../_resources/image12-3.png)
Getting into Uploads:

**Tip** - Modify the cookies to change yourself into admin.

We can modify the URL bar, to search for content and account id:
![image13](../../../../../_resources/image13-2.png)

Enumerating to id=1 will show the admin access ID and name:
![image14](../../../../../_resources/image14-2.png)

We can edit our cookie to the role **admin** and user **34322.** Then we can go to the upload page:
![image15](../../../../../_resources/image15-2.png)

Now there should be some kind of upload web-shell exploit so that we can get a foothold.

Foothold:

Looking inside Kali for **webshells** enables us to locate and find php webshells:
![image16](../../../../../_resources/image16-2.png)

Now we need to upload this "php-reverse-shell.php" to the branding image upload:
![image17](../../../../../_resources/image17-2.png)
This results in:
![image18](../../../../../_resources/image18-2.png)

Now that the target has our php-reverse-shell script, we need to run a netcat listener on our machine and find out a way of executing the
Php file on the target machine.

Starting netcat listener:
![image19](../../../../../_resources/image19-1.png)

We can try to navigate to the file inside the URL bar:
![image20](../../../../../_resources/image20-1.png)

This surprisingly works!:
![image21](../../../../../_resources/image21-1.png)

Privilege Escalation:

First, let's check if Robert has sudo access:
![image22](../../../../../_resources/image22-1.png)

Rats! But using id we can see that Robert is a member of a group named **bugtracker:**
![image23](../../../../../_resources/image23-1.png)

We can check if there is any **binary** within the group:
![image24](../../../../../_resources/image24-1.png)

Then we can check what **privileges** it has:
![image25](../../../../../_resources/image25-1.png)
**If you look carefully, you can see that there is SUID set on the binary.**

**Root:**

Finally we can get root, by executing bugtracker:
![image26](../../../../../_resources/image26-1.png)

Cat doesn't work so we can use **more** instead, root flag is inside root, whilst user flag is inside user:

User flag - f2c74ee8db7983851ab2a96a44eb7981
Root flag - af13b0bee69f8a877c3faf667f7beacf
