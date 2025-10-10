---
title: Gathering Info - HTB
updated: 2023-08-03T17:28:08.0000000+01:00
created: 2023-08-03T17:19:55.0000000+01:00
date modified: Monday, May 13th 2024, 10:19:27 pm
---

- We can't use virus total to look at the IPs/domains. WHOIS is also ineffective. It looks like most passive enumeration is just ineffective.
  - *This is probably because the IP generated is not static and is generated when required.*

- To determine webserver version use **curl -I**
- To determine CMS version use WhatWeb
  - To determine exact CMS version we need to use aggression level 3.
