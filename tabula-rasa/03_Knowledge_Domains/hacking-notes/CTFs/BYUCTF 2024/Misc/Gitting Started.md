---
title: Gitting Started
date modified: Friday, May 17th 2024, 3:20:33 pm
---

A local hacker, TheITFirefly, who started up a blog to talk about his exploits in the tech world, has hidden a flag in the source code for his blog. Luckily, his source code is publicly available in a git repo!

[https://gitlab.com/TheITFirefly/tech-blog](https://gitlab.com/TheITFirefly/tech-blog)

***
## Methodology:

Since we know that we are looking for flags that have the structure of: `byuctf{example_flag}` We can clone the repository and use grep to search for any instance of a flag.

```Bash
git clone https://gitlab.com/TheITFirefly/tech-blog.git # Cloning the repo
grep -r 'ctf{".*"}' tech_blog # This will search the repo for any occurence of the flag.
```

This doesn't return anything. Could it be stored within previous commits, this version might not have the flag. The flag can be found within the commit history:

https://gitlab.com/TheITFirefly/tech-blog/-/commit/294172a06f3075869089f2bff5ea5f90aaeeb821

This should technically work, but it doesn't.
```Bash
git grep --all 'ctf{".*"}'
```
