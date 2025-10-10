---
title: Front-end VS back-end
updated: 2023-04-03T16:19:47.0000000+01:00
created: 2023-04-02T09:12:26.0000000+01:00
---

Front End:

The front end of a web app refers to the components that the client can "see" and access (i.e. what regular users can access). These components are referred to as the **source code** of the web app.

These normally consist of HTML (Hyper-text markup language), CSS (Cascading style sheet) and JavaScript.

- HTML: the main elements of the page, including the title and text.
- CSS: The design and animation of the elements.
- JS: The function that each element has.

Modern web application use a **dynamic design**, meaning that elements shrink and grow to fit the size of a screen (this is because of smartphones/tablets).

If the **front-end** of a web app is poorly written and unoptimized, it can make the web app slow and unresponsive and users can think that their internet is bad or that the server is having issues, whilst the issue is actually on the front-end.

Other important aspects to consider in the front-end are:

- **Visual Concept Web Design**
- **User Interface (UI) Design**
- **User Experience (UX) Design.**

Back End:

The back end of a web application is what drives all the functionality of a web app, everything that is needed for a web app to execute is handled by the back-end. It is often a part which we don't see or directly access, but one in which we depend upon.

There are four key components in the back-end:
![image1](../../../../_resources/image1-104.png)

We can summarise this as:
![image2](../../../../_resources/image2-85.png)

Of course, we can host each components on the back end on its own isolated server, or in isolated containers using technology like Docker. For example, databases can be hosted inside Docker containers - this would keep them logically separated from the back-end server.

The danger is that if the **web server, web application or database** are **compromised,** then the **back-end server** is vulnerable. In a traditional implementation.

The main jobs of the back-end is to:

- Develop the main logic and services of the back end of the web application.
- Develop the main code functionalities of the web application.
- Develop and maintain the back-end database.
- Develop and implement libraries to be used in the web application.
- Implement technical/business needs for the web application
  - i.e. collecting customer information for advertising purposes or monitoring program efficiency across users.
- Implement the main APIs for front end component communication.
- Integrate remote servers and cloud services into the web app.

Securing the front and back end:

Even though in most cases, we don't have access to the back-end, the application is still vulnerable since we can possibly inject harmful commands into the back-end via the front-end.

For example: *If we have a search function that is vulnerable, we can use a SQL injection to access the database, or even gain access of the OS of the server via command injection - possibly giving us root.*

When we have access to the source code - due to a leak or if we are given it in a white box pen test - we can review the code for vulnerabilities.

If we are performing a **black-box pen test -** we need to be more creative - we might find open-source web applications, so we can see the source code of said component. This allows us to see sensitive info that could lead to aiding our progress in exploiting a machine.

We can also perform **Local-File Inclusion**, which allows a user to upload a file that can lead to:

1.  Code execution on the web-server
2.  Code execution on the client side, like executing JS to perform cross site scripting.
3.  Denial of service (DOS)
4.  Disclosure of sensitive information.

The 20 most common mistakes for web devs are:

1.  Permitting invalid data to enter the database
2.  Focussing on the system as a whole
3.  Establishing personally developed security methods
4.  Treating security as your last step.
5.  Plain-test password storage.
6.  Allowing weak passwords
7.  Storing unencrypted data inside databases.
8.  Being too optimistic
9.  Permitting variables in the URL path name.
10. Trusting third-party code
11. Depending on the client-side excessively.
12. Hard-coding backdoor accounts
13. SQL injections
14. Remote file inclusions
15. Insecure data handling.
16. Not encrypting correctly.
17. Not using secure encryption
18. Firewall misconfigurations
19. Ignoring layer 8 of the OSI model
20. Review user actions.

As a refresher the OWASP top 10 is:

![image3](../../../../_resources/image3-71.png)

