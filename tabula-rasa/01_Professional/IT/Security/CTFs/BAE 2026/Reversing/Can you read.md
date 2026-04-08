---
date created: Saturday, February 14th 2026, 1:40:33 pm
date modified: Saturday, February 14th 2026, 1:58:55 pm
---

# Can You Read?

**Points:** 100 pts
**Description:** You don't need to run it, but you can if you like
**File:** You are given the file `re001_ef47f38b385c301dfc4157dd029528f1.exe` a PE32 executable (Windows).
# Method:
## Description & Investigation:

First by performing `strings`, we can see the following:

```Bash
...SNIP...
Enter password:
My voice is my password. Verify me.
Password correct! You rule!
Nope.
...SNIP...
```

Thus, password/flag = `My voice is my password. Verify me.`
## Key Takeaways & Remediation:
- Don't skip steps, The `IsDebuggerPresent` could check for debugger presence and lead you down the rabbit hole of trying to patch the binary.
	- `Strings` and `File` first always, then move on to other tools if needed.
- Use and look at the help sections within the CTF glossary.

