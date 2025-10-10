---
title: Page Fuzzing
updated: 2023-07-25T10:52:28.0000000+01:00
created: 2023-07-25T10:04:59.0000000+01:00
date modified: Monday, May 13th 2024, 10:49:23 pm
---

Extension Fuzzing:

Now that we know we have access to pages like **/blog** and **/forum**, but we only see empty pages with no links. So again we need to fuzz further and figure out if the directories have hidden pages - the first step is to check what kind of pages the website uses.

Common webpage extensions are:

- .html
  - Regular webpages
- .aspx
  - An **active server page** (extended) - normally used in the IIS framework for C# or VB.NET scripts.
- .php
  - **Hypertext Preprocessor** - normally used in Apache frameworks.

Before we start to fuzz, we need to specify what file extension we are looking for - we can use two wordlists: 1 for the websites and 2 for the extensions then execute **FUZZ1.FUZZ2** - however, we don't normally need to do this because we can just fuzz for an index file using **index.\***. Since index pages are on most websites.

(**SecLists has a good wordlist for web extensions called *web-extensions.txt)***

Page Fuzzing:

Once we figure out the page extensions (.php for example) we can fuzz using the file extension:

*ffuf -w /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u [http://SERVER_IP:PORT/blog/FUZZ.php](http://SERVER_IP:PORT/blog/FUZZ.php)*

Extension Fuzzing Example:

1.  We need to figure out what extension exist
    1.  ![image1](../../../../_resources/image1-141.png)
        1.  We can see that there is **index.php**
2.  Now we can look inside of blog for various php files
    1.  ![image2](../../../../_resources/image2-114.png)
    2.  We can see that there is **home.php**

![image3](../../../../_resources/image3-90.png)

