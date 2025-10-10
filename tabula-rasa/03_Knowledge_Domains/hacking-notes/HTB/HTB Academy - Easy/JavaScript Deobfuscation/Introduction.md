---
title: 'Introduction:'
updated: 2023-08-05T22:48:22.0000000+01:00
created: 2023-08-05T22:35:38.0000000+01:00
---

Overview:

Code deobfuscation is an important skill to learn if we want to **analyse code** and perform **reverse engineering.** During both red and blue team activities, we will need to decipher code. Without understand what code is doing, we won't be able to succeed in our attack/defence.

In this example, we will be using JavaScript and de-obfuscating it. So we can read the code and figure out what it does.

Source Code:

Most websites require **JavaScript** to perform functions that are needed to properly to run the website. JavaScript is as powerful as it is potentially dangerous.

We first need to access the source code of the website, so we can uncover the source code that contains all general abilities of the website. *We can access source code using the shortcut **CTRL + U.***

Locating JavaScript:

JavaScript is either stored internally with a **\<script\>** tag or can be written into a separate **.js** file. For example:
![image1](../../../../_resources/image1-161.png)

When we check the **secret.js** file, the code is very complicated and we can’t understand it. E.g.
![image2](../../../../_resources/image2-131.png)

This is an example of **code obfuscation.**
