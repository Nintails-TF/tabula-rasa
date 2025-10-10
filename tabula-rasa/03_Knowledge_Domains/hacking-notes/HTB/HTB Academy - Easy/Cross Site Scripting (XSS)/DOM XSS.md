---
title: 'DOM XSS:'
updated: 2023-08-20T14:26:27.0000000+01:00
created: 2023-08-18T18:07:03.0000000+01:00
---

Introduction:

The final type of XSS is a **non-persistent** type called **DOM XSS** - which is completely ran on the client side. It occurs when JavaScript is used to change the page source thought the **DOM (Document object model).**

Example of DOM XSS:

To do list example, we can send a regular request:
![image1](../../../../_resources/image1-192.png)

We can then check the network tab which shows that no HTTP requests are being made:
![image2](../../../../_resources/image2-158.png)

We can see that the input parameter for the URL is using the **\#** of the item we added, this indicates that the client side is being processed by JavaScript and doesn't reach the back-end - hence we have **DOM-based XSS.**

Furthermore, looking at our page code using **CTRL+U**, we will notice that our test string cannot be found.

Source and Sink:

To understand how a **DOM-based XSS** vulnerability works, we need to understand the concepts of **Source** and **Sink** within objects that are displayed on the page. The **Source** is the javascript object which takes the user input; whilst the sink is the object that is written to.

Some of the more commonly used Javascript sinks used to write DOM objects are:
- Document.write()
- DOM.innerHTML
- DOM.outerHTML

There are also **jQuery** library commands that can write to DOM objects:
- Add()
- After()
- Append()

If a **sink** function write the exact input **without sanitization** then we know that the page is vulnerable to XSS. If we look at the source code of the to do list, we can see that the source is being taken by the task parameter:
![image3](../../../../_resources/image3-123.png)
Then we can see that the page uses **innerHTML** to write the variable inside **task** to the **DOM:**
![image4](../../../../_resources/image4-98.png)

So a DOM-based XSS attack is possible.

DOM Attacks:

If we try the XSS payload for the **Stored or Reflected** XSS attacks, they will not work. This is because innerHTML doesn't allow the usage of **\<script\>** tags. Still there are payloads we can inject that don't use **script** tags:
![image5](../../../../_resources/image5-75.png)

This will create a new HTML image object, which will execute on error the origin of the window, *since no image is present* - **the code will always error:**
![image6](../../../../_resources/image6-52.png)

We can use this to get cookie data as well - using the payload:
\![image7](../../../../_resources/image7-45.png)
