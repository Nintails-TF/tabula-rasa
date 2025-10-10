---
title: 'Decoding:'
updated: 2023-08-06T03:45:28.0000000+01:00
created: 2023-08-06T03:14:06.0000000+01:00
---

Introduction:

After sending our post request like so:
![image1](../../../../_resources/image1-165.png)

We have further obfuscated data in the form of this string. This is often done to make data **less readable for humans** and **less detectable by tools/systems.** So how do we deal with code that is obfuscated like this?

We need to look at the 3 most commonly used text encoders:
1.  Base64
2.  Hex
3.  Rot13

Base64:

**Base64** encoding is usually used to reduce the occurrence of special characters - as all characters encoded in **base64** are represented using **alphanumeric characters along with + and / symbols. Even with data like binary.**

**Spotting base64** is easy, since they only include alphanumeric characters - **critically,** base64 has padding using the = character.

This is because base64 **must** be in a multiple of 4, If the resulting output is only 3 characters long, then a **=** is added on.

ENCODING BASE64:
![image2](../../../../_resources/image2-135.png)

DECODING BASE64:
![image3](../../../../_resources/image3-103.png)

Dealing with other types of encoding:

There are TONS of methods of encoding - though these are the most common, we will also sometimes come across other methods of encoding that we may be unfamiliar with.

*If you face any similar types of encoding first try to figure out the type of encoding, then look for online tools to decode it.*

Some tools can help here like [Cipher Identifier](https://www.boxentriq.com/code-breaking/cipher-identifier). Other than encoding, obfuscation tools also can use **encryption.** Which is encoding a string using a key - this makes it hard to reverse engineer and deobfuscate - doubly so if the encryption key is not stored with the script.
Hex:

Hexadecimal encoding is also popular to use when encoding text, this is when each character is encoded to its **hex order** on the **ASCII table**. (a=61, b=62, etc.).

We can get a full ASCII table using **man ascii** or looking online.

**Spotting Hex** is also not had, since there are only 16 characters used. (0 to 9, a to f).

ENCODING HEX:
![image4](../../../../_resources/image4-80.png)

DEOCDING HEX:
![image5](../../../../_resources/image5-61.png)

ROT13:

ROT-13 or the **Caesar cipher** is an old and common encoding technique that shifts each letter by a fixed number. So ROT-1 would shift each character by 1 (a becomes b, b becomes c, etc). So ROT13 shifts each character forward 13 times.

**ROT13 is harder to spot**. But each charcater is mapped to the same character, so common strings like <http://www>, would become uggc://jjj.

ENCODING ROT13:
![image6](../../../../_resources/image6-40.png)

DECODING ROT13:
![image7](../../../../_resources/image7-34.png)

