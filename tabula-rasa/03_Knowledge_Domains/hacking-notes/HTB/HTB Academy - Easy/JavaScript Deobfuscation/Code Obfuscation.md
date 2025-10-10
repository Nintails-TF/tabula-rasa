---
title: 'Code Obfuscation:'
updated: 2023-08-05T23:23:03.0000000+01:00
created: 2023-08-05T22:48:51.0000000+01:00
---

Advanced Obfuscation:

We can further completely obfuscate the code , for example using <https://obfuscator.io>, we have many more options, like converting **string array encoding** to **base64**:

![image1](../../../../_resources/image1-162.png)

Taking our initial command of:
![image2](../../../../_resources/image2-132.png)

We can convert it into:
**var_0x1ec6=\['Bg9N','sfrciePHDMfty3jPChqGrgvVyMz1C2nHDgLVBIbnB2r1Bgu='\];(function(\_0x13249d,\_0x1ec6e5) ….**

There are many other tools like **JSF, JJ Encode, AA Encode.** But these generally slow down the code lots, so you should only perform this only for a good reason, to bypass web filters or restrictions.

What is obfuscation?:

Obfuscation is a technique used to make scripts or code more difficult to read by humans, but it still functions the same from a technical point of view. This is normally done via **obfuscation tools**, which take code as input and then rewrites code in a hard to read manner.

A common technique used by **code obfuscators** is that code is turned into a dictionary of all words and symbols used within the code and then rebuilds the original code.

(<https://beautifytools.com/javascript-obfuscator.php>)

Use Cases:

There are many reasons why developers would obfuscate code. Common reasons are:

- Hiding code to prevent it from being reused or copied
  - This makes code more difficult to reverse engineer.
- To provide security when dealing with authentication on encryption attacks on vulnerabilities that may be found in code.
  - **However, doing authentication or encryption on the client-side is poor practice, since code is more prone to attacks.**

Attackers also use obfuscation, this is mainly used to **circumvent Intrusion Detection Systems and prevention systems.** So to avoid detection of malicious scripts by programs.

Basic Obfuscation:

Take the following line of code as example:
![image3](../../../../_resources/image3-101.png)

A common way to reduce readability is to use a **JavaScript Minifier.** Code minification involves having a code in one single line of code, it is used with large blocks of code.

(<https://www.toptal.com/developers/javascript-minifier>)

Minified JavaScript code is usually saved with the extension **.min.js.**

Packing JavaScript code:

For example, when we use the Beautify Tools obfuscator, we get the following code:
![image4](../../../../_resources/image4-79.png)

We then should test it inside a console, we can use the web console: <https://jsconsole.com>, to check it still executes correctly.

This type of obfuscation is known as **packing** in which we can see the initial function **"function(p,a,c,k,e,d)".** This is a **packer** obfuscation tool. However, it usually contains a certain order in which the words and symbols of the original code were backed to know how to order them in execution.

Though packing does make it harder to read the code, we can still see the main strings in cleartext.
