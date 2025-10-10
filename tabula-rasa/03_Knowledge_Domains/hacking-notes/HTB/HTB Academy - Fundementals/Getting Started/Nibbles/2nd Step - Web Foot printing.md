---
title: 2nd Step - Web Foot printing
updated: 2022-12-19T11:25:44.0000000+00:00
created: 2022-12-19T09:41:01.0000000+00:00
date modified: Monday, May 13th 2024, 10:20:19 pm
---

We can use **whatweb** to check for any web apps in use:
![image1](../../../../../_resources/image1-82.png)

Looking at the IP in Firefox, we see a simple Hello World webpage:
![image2](../../../../../_resources/image2-64.png)

Checking the source code we see:
![image3](../../../../../_resources/image3-55.png)

Now that we have a sub-domain of the IP, we can try access it using the previous techniques. Using whatweb on our subdomain gives:
![image4](../../../../../_resources/image4-46.png)

We get the following technologies from whatweb:

- HTML5
- jQuery
- PHP (PHPSESSID)
- Nibbleblog

We can now start looking at exploits for these technologies.

GoBuster searching:

We use GoBuster to check for any other pages/directories:
![image5](../../../../../_resources/image5-35.png)

This reveals to us various sub-domains:
![image6](../../../../../_resources/image6-25.png)

We can then check the readme page using cURL:
![image7](../../../../../_resources/image7-20.png)

This tells us that our exploit will probably work, unless the readme is outdated.

Taking Stock:

So far we know:
- The version of Nibbleblog is potentially vulnerable to an authenticated file upload vulnerability.
- We have an admin portal at nibbleblog/admin.php
- The Users.xml file tells us that **admin** is a valid username.
- Brute forcing using tools like **Hydra** will blacklist our IP.

What we did to get access to the admin portal:
- Used an nmap scan to scan for all commonly open ports
  - We found 2 ports - a http (80) port and an ssh (22) port
- Discovered an instance of Nibbleblog
  - We did this via looking at the source code of the initial http server.
- We analysed what technologies were being used using **whatweb**
  - HTML5, PHP, Nibbleblog and jQuery.
- Using **GoBuster** we found *admin.php* which gave us access to the admin portal.
- We browsed several directories that showed us that **admin** is a valid username.
- Found out that IP blacklisting is enabled to prevent us brute-forcing login attempts
- Uncovered clues that lead us to finding the valid admin password **nibbles.**

We can use cURL, instead of manually looking at everything:
![image8](../../../../../_resources/image8-18.png)

Finding Exploits:

Now that we have technologies, we can look at any of the tech that
Exists on the target. Underlying tech like HTML and jQuery is going to
Be harder to exploit than something like Nibbleblog.

We can google "Nibbleblog exploits" and we figure out that there is
An exploit that works with version 4.0.3 that allows us to execute
PHP code.

Then by looking at the **Metasploit** source code of the exploit we see
That we need to get to the /admin.php to authenticate.

To do this we can use GoBuster.

Checking out admin.php:

We can access the admin area and try using default credentials,
Either by using pairs like **admin:admin** and **admin:password**. Or via
Googling the default password for Nibbleblog 4.0.3.

Too many password attempts lead to a lockout and the reset pass
-word function doesn't work.

Looking at the error codes:

Remember the error codes:

**200: OK**
**403: Forbidden access**
**301: Permanent redirect**

By poking around at other subdomains we can access a file named:
*Users.xml*. We can read this into our console using **curl** and **xmllint** to Write the output to a file:
![image9](../../../../../_resources/image9-17.png)

This tells us that **admin** is the username.

Finding the password?:

Here we can use metaknowledge of the box, since it is named *nibbles **and** the site title mentions nibbles **and** in the notification emails.* We can at least try using the password.  

This works on this box, but on other systems, guessing the password isn't always going to work.

We can use a tool like **Hashcat** or we can crawl a website using **CeWL** and generate a wordlist from a site.

What to take away:

*That we need a repeatable and structured way to enumerate into systems.*

*Make sure that you add steps to your enumeration if you encounter something new, perhaps a new tool or method.*

*Make sure to take notes about how you got into the system.*
