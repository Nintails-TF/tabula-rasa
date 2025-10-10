---
title: 'Defacing:'
updated: 2023-08-20T15:50:41.0000000+01:00
created: 2023-08-20T14:38:19.0000000+01:00
---

Injecting the payload:

Let's take for example the following HTML code we want to inject on our target website:
![image1](../../../../_resources/image1-194.png)

*Note that if we want to inject any code - we should test it locally first to make sure it looks the way we want.*

We can then minify the HTML into a single line:

**\<script\>document.getElementsByTagName('body')\[0\].innerHTML = '\<center\>\<h1 style="color: white"\>Cyber Security Training\</h1\>\<p style="color: white"\>by \<img src="https://academy.hackthebox.com/images/logo-htb.svg" height="25px" alt="HTB Academy"\> \</p\>\</center\>'\</script\>**

![image2](../../../../_resources/image2-160.png)

Do note that this won't deleted the original source code and our JavaScript code will execute once the page loads and then change the look of the website.

You could disable JavaScript on your browser and still see the original source.

Introduction:

**Defacing** attacks are popular since hacker groups can deface a website and make it look like they have hacked in, these techniques normally use stored XSS vulnerabilities.

How to deface:

We can use injected JavaScript to make the webpage look the way we want it to. However, defacing websites are normally used to send simple messages (i.e. we hacked you), so the defaced website usually has a simple style.

The main elements we want to change are:

- **Background Colour**
  - *Document.body.style.background*
- **Background**
  - *Document.body.background*
- **Page Title**
  - *Document.title*
- **Page Text**
  - *DOM.innerHTML*

We can use these to quickly write our own page and we can even remove the vulnerable element and make it difficult to reset the webpage.

**Changing backgrounds:**

To change a websites background we need to use the following payload:
![image3](../../../../_resources/image3-125.png)

We can also add a background image too:
![image4](../../../../_resources/image4-100.png)

**Changing Page Title:**

Using the following payload, we can edit the title:
![image5](../../../../_resources/image5-76.png)

**Changing Page Text:**

We can change text elements using JavaScript and the ID of the element we want to change:
![image6](../../../../_resources/image6-53.png)

Frequently, since most websites use **jQuery** - we can also use **jQuery** commands to perform the same tasks, like changing text:
![image7](../../../../_resources/image7-46.png)

In most cases, we just want to change the whole body tag to having some kind of text message - we can edit the whole body using:
![image8](../../../../_resources/image8-39.png)

