---
date created: Friday, January 3rd 2025, 3:00:01 pm
date modified: Friday, January 3rd 2025, 3:25:25 pm
---

# OverTheWire - Bandit

# Introduction:

**Summary:** *Bandit is a wargame for complete beginners, it preaches persistence and fundamentals.*
**SSH Info:** `bandit.labs.overthewire.org:2220` 
**Support:** *Use `man` `--help` and `-h` to get help for commands when you know them but don't know how to use them.*

# Cheat sheet:

- `ssh`
	- `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`: Connecting to the ssh server using `-p` to specify port and `-l` to specify the login username.
	- `ssh bandit0@bandit.labs.overthewire.org -p 2220`: A more lean technique.
`

# Notes:

| Level                                                                       | Notes                                                                                                                                                                                               | Questions             | Password                           |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- | ---------------------------------- |
| [Level 0](https://overthewire.org/wargames/bandit/bandit0.html)             | Use the `-l bandit0` to set username when connecting via ssh.                                                                                                                                       |                       | `bandit0`                          |
| [Level 0 → Level 1](https://overthewire.org/wargames/bandit/bandit1.html)   | `cat` the `readme` file in the `/home/`directory.                                                                                                                                                   |                       | `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If` |
| [Level 1 → Level 2](https://overthewire.org/wargames/bandit/bandit2.html)   | The crux of this problem, is figuring out how to read the filename `-`. Since using `-` in an argument will refer to the STDIN/STDOUT, rather than our file. We can use `cat ./-` to read the file. | What is STDIN/STDOUT? | `263JGJPfgU6LtdEvgfWU1XP5yac29mFx` |
| [Level 2 → Level 3](https://overthewire.org/wargames/bandit/bandit3.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 3 → Level 4](https://overthewire.org/wargames/bandit/bandit4.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 4 → Level 5](https://overthewire.org/wargames/bandit/bandit5.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 5 → Level 6](https://overthewire.org/wargames/bandit/bandit6.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 6 → Level 7](https://overthewire.org/wargames/bandit/bandit7.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 7 → Level 8](https://overthewire.org/wargames/bandit/bandit8.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 8 → Level 9](https://overthewire.org/wargames/bandit/bandit9.html)   |                                                                                                                                                                                                     |                       |                                    |
| [Level 9 → Level 10](https://overthewire.org/wargames/bandit/bandit10.html) |                                                                                                                                                                                                     |                       |                                    |
|                                                                             |                                                                                                                                                                                                     |                       |                                    |
|                                                                             |                                                                                                                                                                                                     |                       |                                    |
|                                                                             |                                                                                                                                                                                                     |                       |                                    |
