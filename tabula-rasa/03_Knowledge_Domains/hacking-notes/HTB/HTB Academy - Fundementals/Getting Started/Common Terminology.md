---
title: Common Terminology
updated: 2022-08-31T19:01:52.0000000+01:00
created: 2022-08-16T14:38:55.0000000+01:00
date modified: Tuesday, May 14th 2024, 12:56:49 pm
---

What is the shell?

The shell is a very common term in infosec. It has multiple meanings, but generally, it refers to the console on a Linux System that allows a user to input commands via a keyboard and passes these instructions to the OS to perform certain instructions.

The *shell* is often used to refer to cmd and windows PowerShell.

Most Linux distros use Bash (Bourne Again Shell) as a shell program - which is an enhanced version of sh. There exists many different shells, like Tcsh, Ksh and Fish Shell.

The term *getting a shell* on a system refers to gaining shell level access to the targeted system - or pwning it. A shell is often obtained by exploiting High or critical vulnerabilities in web applications, networks/services. Or obtaining credentials and logging into the target remotely.

There are 3 main types of shell:

- **Reverse Shell -** Initiates a connection back to a listener from an attack system.
- **Bind Shell -** "Binds" to a specific port on the target system and wait for a connection from our attack system.
- **Web Shell -** Runs OS commands via the web browser, typically these are not interactive or are semi-interactive.

What is a web server?:

A web server is an application that runs on the back-end of a server, which handles all of the HTTP(S) traffic from the client-side browser and then routes it to the destination page. Since they are responsible for connecting end users to various parts of a web app, like logs.tf

Since web apps are public for public interaction, they often end up targeted and can lead to the back-end server being compromised if they suffer from any vulnerabilities.
What is a port?:

A port is a virtual point in which network connections begin and end, think of them as a door or a window on a house. If they remain unlocked, unauthorized access can be achieved. Ports are associated based on the processes and services that they run. e.g.

HTTP messages run on port 80, whilst HTTPS messages go to port 443. Web apps normally run on ports 80 and 443. Ports help computers make sense of the data that they are receiving.

There are two categories of ports:

1.  Transmission Control Protocol (TCP)
    1.  TCP is connection oriented, meaning that there must be a connection between a client and a server before any data is exchanged. The server must be *listening* state awaiting connection requests from clients.
2.  User Datagram Protocol (UDP)
    1.  UDP is a connectionless model of communication, there isn't a handshake like in TCP. UDP is good at being fast and is good for real time systems. Dropping packets is faster than waiting to send out new packets.

OWASP Top 10:

The OWASP (Open Web Application Security Project) lists the top 10 most dangerous vulnerabilities in web applications.

<https://owasp.org/www-project-top-ten/>

1.  Broken Access Control
    1.  Restrictions are not appropriately implemented to prevent users from accessing other users accounts, viewing sensitive data, accessing unauthorized functionality, modifying data, etc.
2.  Cryptographic Failure
    1.  Failures related to cryptography which often leads to sensitive data exposure or system compromise.
3.  Injection
    1.  User-supplied data is not validated, filtered, or sanitized by the application. Some examples of injections are SQL injection, command injection, LDAP injection, etc.
4.  Insecure Design
    1.  These issues happen when the application is not designed with security in mind.
5.  Security Misconfiguration
    1.  Missing appropriate security hardening across any part of the application stack, insecure default configurations, open cloud storage, verbose error messages which disclose too much information.
6.  Vulnerable and outdated components
    1.  Using components (both client-side and server-side) that are vulnerable, unsupported, or out of date.
7.  Identification and authentication failures
    1.  Authentication-related attacks that target user's identity, authentication, and session management.
8.  Software and Data integrity failures
    1.  Software and data integrity failures relate to code and infrastructure that does not protect against integrity violations. An example of this is where an application relies upon plugins, libraries, or modules from untrusted sources, repositories, and content delivery networks (CDNs).
9.  Security logging and monitoring failures
    1.  This category is to help detect, escalate, and respond to active breaches. Without logging and monitoring, breaches cannot be detected.
10. Server side request forgery.
    1.  SSRF flaws occur whenever a web application is fetching a remote resource without validating the user-supplied URL. It allows an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall, VPN, or another type of network access control list (ACL).

