---
date created: Saturday, February 14th 2026, 2:16:36 pm
date modified: Saturday, February 14th 2026, 3:06:21 pm
---

# It's the Code Breaker

**Points:** 150pts
**Description:** You don't need to run it, but you can if you like
**File:** You are given the file `re002_b26b89003aa00c6ac7f87c952b9367a3.exe` (PE32 executable, Windows).

# Method:
## Description & Investigation:

First, `strings`reveals:
```Bash
strings re002_b26b89003aa00c6ac7f87c952b9367a3.exe

...SNIP...
@.reloc
BSJB # BSJB is the .NET metadata signature.
v2.0.50727 # This is the .NET version 2.0.50727
...SNIP...

..SNIP...
_CorExeMain # This tells the PC that we are running a .NET program
mscoree.dll
...SNIP...


```

So, we know that the program is a `.NET` program for windows. 
## Interrogating a .NET Executable:

Using `dotPeek`, we can turn the `.exe` back into readable classes. We first do this by navigating from the `Assembly -> Namespace`. We then can see the following code:

```cs
 if (Console.ReadLine() == Encoding.UTF32.GetString(new byte[64 /*0x40*/]
    {
      (byte) 84, 
      (byte) 0,
      (byte) 0,
      (byte) 0,
      // Only showing the first letter, as it gets too long showing them all.
...SNIP... 
```

The encoding of `Encoding.UTF32` uses 4 bytes per letter. So we have 3 padding bytes (`0x0`) for each letter. If we map the bytes to the corresponding ASCII value: we get the following:

```
Byte 01-04: [84, 0, 0, 0]  ->  84  -> 'T'
Byte 05-08: [111, 0, 0, 0] -> 111  -> 'o'
Byte 09-12: [111, 0, 0, 0] -> 111  -> 'o'
Byte 13-16: [32, 0, 0, 0]  ->  32  -> ' ' (Space)
Byte 17-20: [109, 0, 0, 0] -> 109  -> 'm'
Byte 21-24: [97, 0, 0, 0]  ->  97  -> 'a'
Byte 25-28: [110, 0, 0, 0] -> 110  -> 'n'
Byte 29-32: [121, 0, 0, 0] -> 121  -> 'y'
Byte 33-36: [32, 0, 0, 0]  ->  32  -> ' ' (Space)
Byte 37-40: [115, 0, 0, 0] -> 115  -> 's'
Byte 41-44: [101, 0, 0, 0] -> 101  -> 'e'
Byte 45-48: [99, 0, 0, 0]  ->  99  -> 'c'
Byte 49-52: [114, 0, 0, 0] -> 114  -> 'r'
Byte 53-56: [101, 0, 0, 0] -> 101  -> 'e'
Byte 57-60: [116, 0, 0, 0] -> 116  -> 't'
Byte 61-64: [115, 0, 0, 0] -> 115  -> 's'

Result: "Too many secrets"
```
## Key Takeaways & Remediation:

- Whilst this method bypassed a `strings` check, by converting the password into a byte array and using UTF-32 encoding, it's security by obfuscation.
- Since .NET compiles into a Common Intermediate Language (CLI) it contains metadata about it's structure. (`BSJB, _CoreExeMain, mscoree.dll`).
	- This makes .NET easier to reverse engineer than other native forms of code, like C++.
	- You can use tools like: [Dotfuscator Community Edition](https://learn.microsoft.com/en-us/visualstudio/ide/dotfuscator/?view=visualstudio) to better obfuscate your code.
- Hardcoded credentials shouldn't be stored in program code.
	- Using environment variables is a better way - that isn't perfect since the secret still lives in RAM/Memory. But it is much harder to figure out.
