---
title: Solving PWN Challenges
date modified: Thursday, May 16th 2024, 11:42:07 am
---

## Introduction

When talking pwn problems we have various tactics.

1. Understand the program flow and run it.
2. Understand the source code, or reverse engineer the resource code if we don't have source code.
	1. We can use Ghidra, IDA, GEF/GDB, and knowledge of assembly to reverse engineer code.
3. Spot bugs and vulnerabilities
	1. Bad design, logical errors, poor error checking
	1. Stack Buffer overflow, GOT hijacking, Format strings attack, FSOP, etc.

PWN challenges are generally dependent on the system you are trying to break into, e.g. Windows, Linux, C++ programs, Sandbox escaping, Different CPU architectures, different kernels.

## Resources:

- Resource to learn pwn
	- [Live Overflow Binary Exploitation and memory corruption playlist](https://www.youtube.com/playlist?list=PLhixgUqwRTjxglIswKp9mpkfPNfHkzyeN)
- Tools for pwning
	- [pwntools](https://github.com/Gallopsled/pwntools#readme)
		- Pwntools is used to write scripts and exploits quickly and easily.
- Resources to practice pwn
	- https://pwnable.kr/
	- https://pwnable.xyz/challenges/
- 