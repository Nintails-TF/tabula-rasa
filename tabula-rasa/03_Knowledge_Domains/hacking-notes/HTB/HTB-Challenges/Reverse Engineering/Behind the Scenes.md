---
title: Behind the Scenes
date modified: Monday, May 13th 2024, 8:23:33 pm
---

We are given a file, which is an executable:
![image1](../../../../_resources/image1-207.png)

Trying to run the executable gives:
![image2](../../../../_resources/image2-173.png)

We can use ltrace to trace library calls:
![image3](../../../../_resources/image3-138.png)

We get SIGILL - Illegal instruction - this means that this problem is caused using UD2A or UD2 assemble instruction - it is an invalid opcode which is used to throw an exception - a bit like a breakpoint.

We then input the correct password:
![image4](../../../../_resources/image4-113.png)

If we look at Ghidra then filter for UD2 or UD2A - we can decompile the code:
![image5](../../../../_resources/image5-87.png)

So we need to figure out what **invalidInstructionException**() does. Using CTRL+SHIFT+E we can filter for UD2 and we can see it inside our main of our program:
![image6](../../../../_resources/image6-62.png)

The code hasn't been disassembled correctly, so we can disassemble it by selecting the code and disassembling it:
![image7](../../../../_resources/image7-55.png)
We can see that the flag is being constructed somehow in this code.

We can now look for strncmp to see what strings are being copied:
![image8](../../../../_resources/image8-48.png)
![image9](../../../../_resources/image9-41.png)
![image10](../../../../_resources/image10-34.png)
![image11](../../../../_resources/image11-26.png)

This gives us the code: **Itz_0nLy_UD2**
