---
title: Level 7 -> Level 8
updated: 2022-10-18T22:14:49.0000000+01:00
created: 2022-07-21T18:29:14.0000000+01:00
---

Commands:

**Grep** is used to print lines that match a pattern.
**Sort** is used to sort lines of text files
**Uniq** is used to report or omit repeated lines
**Base64** is used to encode or decode data.
**Tr** is used to translate or delete characters
**Tar** is used to archive files.
**Gzip** is used to compress or expand files
**Bzip2** is used to compress, decompress and recover bzip2 files.
**Xxd** is used to make hexdumps or reverse hexdumps.

It looks like that Grep is the best tool for the job here.

![image1](../../../_resources/image1-218.png)

We can look for the word millionth using grep.

![image2](../../../_resources/image2-184.png)

This gives us the password.
![image3](../../../_resources/image3-146.png)

It looks like we need to locate the file data.txt and then find the password next to the world millionth.

Well the data.txt is located when we first log in using ssh.

