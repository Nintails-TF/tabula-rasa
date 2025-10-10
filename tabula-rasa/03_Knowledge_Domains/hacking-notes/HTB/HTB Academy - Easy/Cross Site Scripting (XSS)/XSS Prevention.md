---
title: 'XSS Prevention:'
updated: 2023-08-21T16:16:59.0000000+01:00
created: 2023-08-21T10:36:47.0000000+01:00
---

Introduction:

Now that we know the different types of XSS, how to find them and how to exploit them. We should learn how to defend and remediate against XSS issues.

XSS vulnerabilities are mainly linked in two parts of a web app, the **source and sink.** The source is like the user input field and the sink is the field that displays data. So we need to secure both the source and sink on both the front and back-end.

Front End:

When dealing with the front end, we need to make sure to sanitize and validate user input, this is often done using JavaScript.

For example the regular expressions statement used on the email field in the activities will not allow us to submit the form if the format for the email is invalid:
![image1](../../../../_resources/image1-197.png)
If the value is false, then the form is not submitted.

Input Sanitization:

In addition to validating the user input we need to make sure we don't allow any **JavaScript code** to be entered into fields as well, we can use the **DOMPurify** JS library to do this:
![image2](../../../../_resources/image2-163.png)

This will escape any characters by adding a backslash to them so that the user cannot send input with special characters to prevent DOM XSS vulnerabilities.

Direct Input:

Finally, we shouldn’t use user input within certain HTML tags, like:
![image3](../../../../_resources/image3-128.png)

Since they can be used to inject malicious JavaScript code.

Server Configuration:

In addition to the other defensive measures, we should make sure to configure our back-end server to prevent XSS attacks:

- Using HTTPS across the entire domain
- Using XSS prevention headers
- Using the appropriate **Content-Type** for the page, like **X-Content-Type-Options=nosniff**
- Using **Content-Security-Policy** options like **script-src 'self'**, which only allows locally hosted scripts and nothing remote.
- Using the **HttpOnly** and **Secure** cookie flags to prevent JavaScript from reading cookies and only transporting them over HTTPs.

A strong **Web Application Firewall** (WAF) can also significantly reduce the chances of XSS attacks, since it will detect and block any type of injection that goes through HTTP requests, certain frameworks like ASP.NET also have built in XSS protection.

Additional functions that should be avoided:

We should also avoid direct user input in the following functions:
![image4](../../../../_resources/image4-103.png)
And the jQuery functions:
![image5](../../../../_resources/image5-79.png)

*Basically, any function which writes raw text to the HTML code - alternatively we could search source code for these to look and test for XSS.*

Back-end:

We also need to protect the back-end from XSS too, even if we have client-sided validation it isn't enough because it can be bypassed or circumvented. So we should implement features like **input/output sanitization and validation, proper server configuration and back-end tools** to prevent XSS vulnerabilities.

Input Sanitization:

This is similar to the front-end, we use regular expressions or library functions to ensure that the input field contains what we expect - if it doesn't match we reject the request.

For example, using email validation on PHP:
![image6](../../../../_resources/image6-56.png)

We also can use certain libraries when handling POST and GET requests, an example of this is **addslashes:**
![image7](../../../../_resources/image7-49.png)

We can also use DOMPurify similarly to what we did with the front end, if NodeJS is used as a backend:
![image8](../../../../_resources/image8-42.png)

In any case, **direct user input should never be displayed directly on the page.** As this can lead to XSS vulnerabilities.

Output HTML Encoding:

Output encoding, means that we are encoding any special characters into their HTML codes (e.g. \$ becomes %24). This is helpful because we can display the user input with introducing XSS vulnerabilities.

We have two libraries which can do this:

- For PHP - **htmlentities**
  - ![image9](../../../../_resources/image9-35.png)
- For NodeJS - **htmlentities**
  - ![image10](../../../../_resources/image10-29.png)

