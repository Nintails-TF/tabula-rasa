---
title: 'Deobfuscation:'
updated: 2023-08-06T02:38:09.0000000+01:00
created: 2023-08-05T23:23:18.0000000+01:00
---

Just as there are tools to obfuscate code automatically, there are tools to beautify code and deobfuscate code automatically.

Beautify:

The most basic method of beautification is using **Browser Dev Tools.** If we are using Firefox, we can open our browser debugger with **CTRL+SHIFT+Z** and then we can access our script in the raw form. For instance:
![image1](../../../../_resources/image1-163.png)

We can also use many online tools or code editor plugins like [**Prettier**](https://prettier.io/playground/) or **[Beautifier](https://beautifier.io/).** After beautification, we can see:
![image2](../../../../_resources/image2-133.png)

The issue with this is that the code is still not easy to read. *This is because the code was **minified** and **obfuscated**. So we need to also deobfuscate it.*

Deobfuscation:

There are many tools we can use to deobfuscate JS code and make it more human-understandable. A good tool is [**JSNice.**](http://www.jsnice.org/) We can enter JS and "Nicify" it.

We need to make sure to de-select "Infer types" to reduce comments cluttering the code and we should avoid any whitespace or empty lines. Nicifying our JS gives us:
![image3](../../../../_resources/image3-102.png)
Note that the code is still packed, we can use console.log on the return value to get information rather than sending it or opening it.

Reverse Engineering:

The more code becomes obfuscated and encoded, the harder it is for automatic tools to clean it up - especially if a custom obfuscation tool is used.

In these cases we would have to **manually reverse engineer** the code to understand how it was obfuscated and its functionality. The module **Secure Coding 101** can help with learning this.

Checklist:

1.  Go to an online deobfuscator
2.  Run the JS in a console and log the return statement.
