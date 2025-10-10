---
title: Introduction
updated: 2023-08-01T14:59:36.0000000+01:00
created: 2023-07-31T18:55:07.0000000+01:00
date modified: Monday, May 13th 2024, 11:14:28 pm
---

Introduction:

The first step of any serious **penetration test** involves simulating being an external attacker with **no internal knowledge** so we need to perform **information gathering** to ensure that we can accurately find flaws and vulnerabilities.

If we rush the information gathering stage, we can end up missing **holes in the armour**. That enumeration would uncover. Taking the example of a penetration test process:
![image1](../../../../_resources/image1-149.png)
*Fig 1. Penetration test process.*

As we can see, **information gathering** is at the start of an attack, it enables us to:

- Understand the attack surface.
- Figure out what technologies are being used.
- Occasionally, discover dev environments and forgotten/unmaintained infrastructure.
  - This can lead to **internal network access.**

As we discover assets (subdomains, vhosts, etc.) we need to fingerprint what technologies are in use, enumerate for hidden pages/directories, etc. All of which can lead to discovering another sub-domain in which we can go deeper into the system.

**For example,** we can think of fuzzing for new subdomains during our pen test via the SSL certificate. However, if we take a closer look - we may see that subdomains use different technologies than the initial main website. Then sub-domains and virtual hosts are created to perform other tasks.

***It is essential we find out what technologies are in use, what purpose they serve and how they work.***
Information to gather:

What kinds of information should we try to gather during a pen test? The key areas are:

1.  **Domains and sub-domains**
    1.  When we perform a pen test we are given a single domain or a list of domains. *Many organisations do not have accurate knowledge about what is actually running and what is exposed to the public.* **This is essential part of reconnaissance - we can come across new subdomains that we can attack.**
    2.  Bug bounty programs often set scope as: \***.google.com** meaning that all subdomains of google are fair play and are in scope *(acme.google.com, admin.google.com).* We can also uncover **nested sub-domains** e.g. *dev.admin.google.com* which looks like an enticing target.
    3.  We can search for sub-domains both **actively** and **passively.**

2.  **IP ranges**
    1.  Unless our scope is very limited, we will want to find out as much as possible about our target. Finding additional IP ranges owned by our target can lead to **discovery of other domains and sub-domains** which makes our attack surface larger.

3.  **Infrastructure**
    1.  We want to learn about what **technology stack** our target is using. For example, are all applications ASP.NET? Do they use Django, PHP or flask? What web services or APIs are being used? Are they using a CMS? (WordPress, Joomla, Drupal)
    2.  Also, what webserver is in use - IIS, Nginx, Apache? What versions of these webservers are running? What kinds of back-end databases are in use? (MSSQL, MySQL, PostgreSQL).
    3.  **We want to check all of these for outdated software and possible holes in security.**

4.  **Virtual Hosts**
    1.  Finally, we want to check vhosts, which are similar to sub-domains but indicate that an organisation is hosting multiple applications on the same web server.

Information gather can be done in one of two ways:

**Passive information gathering -** this method is undetectable and uses public data via *search engines, certificate information, etc.* to gather information that we can use as inputs during the active information gathering phase.

**Active Information gathering** - this method is more aggressive, you'll likely trip alarm bells if you aren't authorised to test the website. These include - *port scanning, DNS enumeration, directory brute-forcing, vhost enumeration and crawling/spidering.*

Closure:

We need to present our findings in a readable manner, it is also worth it working on bug bounty programs and performing reconnaissance to practice information gathering skills.

Ideally we should develop our own **repeatable methodology** and creating our own tools or automate existing tools.

