---
title: 'Appointment:'
updated: 2022-09-10T12:14:46.0000000+01:00
created: 2022-09-10T09:05:13.0000000+01:00
---

What response code is given for "Not Found" errors?:

*404 status code.*

What switch do we use with GoBuster to specify we're looking to discover directories, and not subdomains?

*We use the **dir** flag to enumerate for directories.*

Getting the flag:

Using nmap, we find out that port 80 (HTTP) is open and is running Apache httpd 2.4.38 ((Debian)).

Using GoBuster and the common.txt wordlist:  

![image1](../../../../../_resources/image1-56.png)
We get the following URLs:

![image2](../../../../../_resources/image2-42.png)

Looking at the directories we can see the website is running:

- Animsition - A jQuery plugin for page transitions
- Bootstrap (v4.0.0 beta) - A CSS framework
- Countdowntime
- CSS-hamburgers
- jQuery 3.2.1
- Perfect-scrollbar
- Select2
- Font-awesome-4.7.0

Now we can check searchsploit if they have any vulnerabilities, which they do not.

Then trying to log in using default credentials:
![image3](../../../../../_resources/image3-35.png)
Also doesn't work, it appears like the crux of this task is to use a SQL injection to bypass the login or retrieve our flag.

(Do note that a brute force method could of also been used here and would have been a valid approach).

The tags listed indicate we need to know about SQL, SQLi and MariaDB.

What does SQL stand for?:

*Structured Query Language, it is used for filtering databases to return specific patterns of data. Like all people aged 18+ in a database of people.*

What is one of the most common types of SQL vulnerabilities?:

*SQL injections, which is the usage of SQL code executed or injected to the database via a web page. This can arise due to un-sanitised user input or other vulnerabilities.*

What does PII stand for?:  

Personally Identifiable Information, it is data that can identify an individual person. It includes information like names, addresses, emails, telephone numbers, social security numbers and credit card numbers.

What does the OWASP Top 10 list name the classification for this vulnerability?:

[***A03:2021-Injection***](https://owasp.org/Top10/A03_2021-Injection/)

What service and version are running on port 80 of the target?:

*Using nmap we find out that **Apache httpd 2.4.38 ((Debian))** is running on port 80.*

What is the standard port used for the HTTPS protocol?:

*Port 443.*

What is one luck-based method of exploiting login pages?

*Brute-Forcing, which is the act of randomly guessing strings of credentials until the login is accepted. You could theoretically get a password within a few seconds, but more often than not, it will take a very long time to brute force secure passwords.*

What is a folder called in web-application terminology?

*It is called a directory.*

SQL Injection:

Note that trying to submit a username and password via the login form on the web page, but we are also able to specify a SQL query if there is no input validation. Special characters like \# and ' can be used to modify queries in the SQL database.

Single quotes (') can be used to specify the exact that they needs to be retrieved from the SQL database.
Hashtags (#) can be used to make comments.

Using a username of:
![image4](../../../../../_resources/image4-27.png)

And any password will allow us to try and inject this code and just check for if any username exists and skips passwords. Note that any valid username would allow this code to work. This works because:

![image5](../../../../../_resources/image5-18.png)

Because there is a lack of input validation allowing us to skip the password. Thus giving us the flag:
E3d0796d002a446c0e622226f42e9672
