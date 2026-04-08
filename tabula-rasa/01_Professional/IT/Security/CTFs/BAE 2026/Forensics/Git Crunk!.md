---
date created: Saturday, February 14th 2026, 11:17:26 am
date modified: Saturday, February 14th 2026, 11:47:30 am
---

# Git Crunk!

**Points:** 100
**Description:** People should be careful where they leave things.
**File:** A 7zipped file (`for002_489d2f6741356e021110269e5a67cecf.7z`) contains the directory of `secretplans` which contains: `CV.txt, mugshot.jpg, TODO.txt`

# Method:

First, to gain access to the folder:
```Bash
7z x for002_489d2f6741356e021110269e5a67cecf.7z # Deflate the compressed data
# x keeps the file path/sub folders.
```

The files, describe a villain known as **Killface.** 

Since the challenge hints at git, I'm thinking that `.git` file would exist and can be potentially interrogated:
```Bash
ls -la          
total 56
drwx------ 3 kali kali  4096 Jul 16  2012 .
drwxr-xr-x 3 kali kali  4096 Feb 14 06:20 ..
-rw-r--r-- 1 kali kali   369 Jul 16  2012 CV.txt
drwx------ 7 kali kali  4096 Jul 16  2012 .git
-rw-r--r-- 1 kali kali 35182 Jul 16  2012 mugshot.jpg
-rw-r--r-- 1 kali kali   125 Jul 16  2012 TODO.txt

```

## Accessing Information from the Git Log:

By using looking at the git commit history we can see that the password is actually revealed to us through the `Oops!` commit:

```Bash
git log --patch

...SNIP...
commit bdc98db8a2d3018b8063ac2a67e1b168768d95eb
Author: timpwn <timpwn@laptop>
Date:   Mon Jul 16 17:21:01 2012 +0100

    Oops!

diff --git a/TODO.txt b/TODO.txt
index cde91d7..8a5344c 100644
--- a/TODO.txt
+++ b/TODO.txt
@@ -1,5 +1,3 @@
 1. Finish Annihilatrix.
 2. Drive planet into sun.
-3. Profit!
-
-Remember: Password is 'Frisky Dingo'!
\ No newline at end of file
+3. Profit!
\ No newline at end of file
```

## Learning Lesson:

1. Git is a timeline, even if you commit then delete sensitive data, git will keep it in the history.
2. Make sure to use `.gitignore` to avoid tracking commits to sensitive files or passwords.
3. If you do commit your whole project folder by accident, use tools like: [git-filter-repo](https://github.com/newren/git-filter-repo) or [BFG Repo-Cleaner](https://github.com/rtyley/bfg-repo-cleaner)