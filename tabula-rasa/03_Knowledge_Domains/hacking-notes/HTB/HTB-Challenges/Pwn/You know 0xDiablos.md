---
title: You know 0xDiablos
date modified: Thursday, May 16th 2024, 4:29:37 pm
---

## Introduction

We are given a file called **vuln.** We can make this an executable and try running it:
```Bash
./vuln
You know who are 0xDiablos: 
a
a
```

We are allowed to input some data into the program. Lets open the program in **radare2** and start to analyse it.

## Using radare2 or Ghidra

First we can open the file in radare2, the **aa** flag starts automatic analysis, we can then view the assembly using **pdf.**
```Bash
radare2 Vuln
aa 
pdf
```

We could also use Ghidra in this case.

