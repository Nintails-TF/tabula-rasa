---
title: 'WPScan Overview:'
updated: 2023-07-20T18:54:37.0000000+01:00
created: 2023-07-20T01:37:23.0000000+01:00
---

Practical Example:

If we want to perform a Wpscan against a target we can perform:
![image1](../../../../_resources/image1-130.png)

We get tons and tons of info about what could be vulnerable to attack. It really is worth saving it to a file.
Introduction:

WPScan is an automated scanner for WordPress scanner and enum tool. It determines various themes and plugins used by Wordpress site are outdated or vulnerable. *We can install this using **gem:***
![image2](../../../../_resources/image2-106.png)

A couple of valuable options are:

- -o
  - *Saves output to file.*
- -e
  - *Specifies enumeration processes - so you can check for specific plugins and ID ranges.*
- -P
  - List of passwords to use during the password attack.
- -U
  - List of usernames to use during the password attack.
- -t
  - How many threads the scanner can use - default is 5.

We can enhance our WPScan via getting an API token from [WPVulnDB](https://wpscan.com/) - which WPScan uses to scan for vulnerabilities and use POCS and reports - with the free plan you get **25 requests** per day.

We can then supply this API token using **--api-token \[blahblah\]**

Enumerating a website using WPScan:

We use the **--enumerate** flag to enumerate various components of a WordPress application like themes, plugins and users, by default WPScan will look at everything, but if we want a faster search we can restrict the search. For instance:

- --enumerate ap
  - *This will look at all Wordpress plugins.*
