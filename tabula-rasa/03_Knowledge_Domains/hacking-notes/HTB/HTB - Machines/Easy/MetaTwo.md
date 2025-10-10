---
title: MetaTwo
updated: 2023-04-08T00:12:39.0000000+01:00
created: 2023-04-07T23:36:16.0000000+01:00
date modified: Monday, May 13th 2024, 10:16:10 pm
---

Enumeration:
Nmap Scan:
![image1](../../../../_resources/image1-49.png)

We now know:

- FTP port on port 21.
- SSH port on port 22.
- HTTP port on port 80.

We need to resolve this in our etc/hosts file. So we can view the HTTP port:
![image2](../../../../_resources/image2-37.png)

Now we can open the website in BURP and start to poke and prod at it:

- Landing Page: <http://metapress.htb/>

We should search for alternate domains to check for some kind of admin portal. We can use GoBuster for this:

We find the following interesting domains:

- Robots.txt
  - This shows us that there is a wp-admin (WordPress) portal we can get to.
  - This also reveals an **admin.php** file, this worth a serious look.
  - Finally we have a **sitemap**? What is that?
  - ![image3](../../../../_resources/image3-30.png)
- <http://metapress.htb/wp-login.php>
  - This is the admin login for the word press portal
- <http://metapress.htb/feed/rdf/>
  - This gives us some kind of feed?
  - We also get to download an atom feed?

Target details:

IP - 10.10.11.186  

**Technologies - (Wappalyzer):**
![image4](../../../../_resources/image4-23.png)

Ideas:

1.  Could think about manipulating the PHPSESSID (PHP cookie) to that of a super-user.

Events:

We can book events via a form, there should be someway of manipulating this to do something:
![image5](../../../../_resources/image5-15.png)

