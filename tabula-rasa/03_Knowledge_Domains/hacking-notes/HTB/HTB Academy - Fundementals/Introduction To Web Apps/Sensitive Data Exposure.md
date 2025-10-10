---
title: 'Sensitive Data Exposure:'
updated: 2023-04-06T12:35:13.0000000+01:00
created: 2023-04-06T10:23:49.0000000+01:00
---

Introduction:

All of the **front end** components are executed on the client side, so if they are vulnerable, they don't directly pose a threat to the **back end**. This puts the end-user in danger of being attacked and exploited.

This means that admin users can be exploited and unauthorized access to sensitive data can be accessed. This means that we need to test front-end components for potential vulnerabilities, so that we don't get hit by vulnerabilities that allow us to - per say - exploit an admin portal.

Sensitive Data Exposure:

***Sensitive Data Exposure** refers to the availability of sensitive data In clear-text to the end-user.* The main method in which sensitive data is exposed via the **source code**. The HTML source code of the application is the usual route for this.

We often use the **view page source,** to check this. We sometimes can find **creds or hashes** hidden within the source code, or other details. Other sensitive information may include:

- Exposed links
- Exposed directories
- Exposed user info

*We can use this information to further exploit the web app supporting infrastructure - **web server, database servers, main server.***

This allows us to look for **low-hanging fruit.**

Front end source code:

Developers should only run web applications functions, without any extra code or comments that are not necessary for the web app to function. We need to make sure that the code is reviewed to make sure that there isn't any **sensitive data**.

Developers need to review client-side code to ensure that no unnecessary comments or hidden links are left behind.

Also **JavaScript obfuscation** can be used to reduce the ability of automated tools from locating these types of data.
