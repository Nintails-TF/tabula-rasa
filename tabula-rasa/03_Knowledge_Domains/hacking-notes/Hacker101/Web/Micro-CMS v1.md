---
title: Micro-CMS v1
updated: 2023-01-22T12:49:50.0000000+00:00
created: 2022-08-02T17:42:38.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:11:56 pm
---

Micro-CMS v1:
Resources:

<https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>

02 August 2022
17:42
Initial Exploration:

So the website is a plain website that allows the user to create new pages and edit previous pages.
![image1](../../../_resources/image1-237.png)

Looking at the source code of markdown test we can see that the image of a kitten isn't displayed correctly:
![image2](../../../_resources/image2-194.png)
The link: <https://static1.squarespace.com/static/54e8ba93e4b07c3f655b452e/t/56c2a04520c64707756f4267/1493764650017/>

It is possible to edit this image to return something critical?

Maybe user input isn't sanitised and you can input some kind of attack that could expose more resources or flags when a certain command is executed?

It would be nice to be able to find all of the URLs on a server. I wonder if there is a tool for that?

When we create a page we get sent to page 8?

<https://3919e937d2658f01c151228de816a9f1.ctf.hacker101.com/page/8>
<https://3919e937d2658f01c151228de816a9f1.ctf.hacker101.com/page/edit/8>

When changing the URL and looking at page 5 we get the following:

![image3](../../../_resources/image3-153.png)

We then are able to edit page 5 and we get the first flag:
![image4](../../../_resources/image4-122.png)

^FLAG^21ed1f9fd4dba7d82658932506920854469cbd56b3b038d6cff6fcda49ed0dc8\$FLAG\$
Using BURP:

Looking at BURP we can see that there is a couple High severity bugs found on the website, Those being:

- External Service interaction - The website can be used as a proxy to attack other services

- Web Cache poisoning - The usage of a custom HTTP header can be manipulated to send malicious responses

- Server-side template injection - The template engine Twig can have template directives injected in allowing code execution.

- SQL injection - a SQL database file can be controlled via carefully crafted user input to send a query and retrieve/delete/tamper with the database.

- OS command injection - Shell metacharacters can be injected and modify commands that can be sent to the server.

