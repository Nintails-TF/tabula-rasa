---
date created: Wednesday, July 2nd 2025, 5:00:54 pm
date modified: Saturday, July 26th 2025, 2:13:37 pm
---

# Solutions:

## Level 1 → Level 2:

The crux of this problem, is figuring out how to read the filename `-`. Since using `-` in an argument will refer to the STDIN/STDOUT, rather than our file. We can use `cat ./-` to read the file.

### Standard In and Out:



***
## Level 2 → Level 3

### Solution:

We need to use double quotes to wrap the filename like so: `cat "my file name.txt"`, since the parser by default uses whitespace. 

If we were to instead use the command of: `cat my file name.txt` the shell will treat this as three separate files/directories ("my", "file", "name.txt"), these don't exist. So the cat program cannot read them as there is `No such file or directory`.

Alternatively, you can use backslashes: `cat my\ file\ name.txt` this works by treating the next character literally, rather than as a delimiter.

Single quotes work too: `cat 'my file name.txt'`, though double quotes are more commonly used since they allow variable expansion when needed. So single quotes are a useful tool in complex strings or filenames, but not here.

### Single VS Double Quotes:


***