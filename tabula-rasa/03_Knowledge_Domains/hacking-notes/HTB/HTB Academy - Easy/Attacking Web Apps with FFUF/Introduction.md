---
title: Introduction
updated: 2023-07-25T09:00:29.0000000+01:00
created: 2023-07-23T17:14:37.0000000+01:00
date modified: Monday, May 13th 2024, 10:48:09 pm
---

Wordlists:

Wordlists when used in fuzzing are very similar to **password dictionary attacks** in that we will not reveal every webpage since this isn't a brute force method - since pages on specific websites will have random or unique names.

In general, we do get most pages (90% success rate on certain websites). Again, there is no need to make our own wordlists we can simply use something like **SecLists** which will give us wordlists for fuzzing and other attacks.
There are many web fuzzing tools, FFUF is a common and reliable web fuzzer, which we will explore in the context of:

- Directory Fuzzing
- File fuzzing
- Identifying hidden vhosts.
- Fuzzing for PHP parameters
- Fuzzing for parameter values

Other web fuzzers (GoBuster, ferox buster, wfuzz) perform a similar role with some slight feature differences.

Why do we need fuzzers?:

Web fuzzing important as it enables us to automatically search for components of a web app, so when we use a wordlist to fuzz a website we check if a page exists with the name from our wordlist. If we get the response code 200, then **usually** we know that a page exists on the webserver and we can take a look.

By fuzzing, we can access more pages in the website and further enumerate and look for holes in web apps.

What is Fuzzing?:

**Fuzzing** refers to the technique of sending various types of user input to an interface (website, database, program) and checking how the interface reacts. If we are fuzzing for **SQL injections** we would send common injections and special characters to see how the server would handle the request.

If we fuzzed a binary (.exe/program) for a buffer overflow. We would be sending long strings and incrementing their length to see if or when the binary would break down.

