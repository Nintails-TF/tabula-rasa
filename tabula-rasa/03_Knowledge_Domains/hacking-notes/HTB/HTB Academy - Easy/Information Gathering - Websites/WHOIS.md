---
title: WHOIS
updated: 2023-08-01T16:02:55.0000000+01:00
created: 2023-08-01T15:00:04.0000000+01:00
date modified: Sunday, September 1st 2024, 9:29:16 am
---

Parsing WHOIS:

We get tons of information from the WHOIS lookup, but the key information is:

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 79%" />
</colgroup>
<thead>
<tr class="header">
<th>Organisation</th>
<th>HACKTHEBOX</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Locations</td>
<td>Middlesex, Hayes, UB3 9TR</td>
</tr>
<tr class="even">
<td>Domain Email Address</td>
<td>Admin Email: 64464a31-4d72-4e91-a951-109f65f6f6aa@identity-protect.org</td>
</tr>
<tr class="odd">
<td>Register Email Address</td>
<td><p>Registrant Email: 64464a31-4d72-4e91-a951-109f65f6f6aa@identity-protect.org</p>
<p></p></td>
</tr>
<tr class="even">
<td>Phone Number</td>
<td><p>Registrant Phone: +44.1483307527<br />
Admin Phone: +44.1483307527</p>
<p></p></td>
</tr>
<tr class="odd">
<td>Language</td>
<td>English</td>
</tr>
<tr class="even">
<td>Registrar</td>
<td>Amazon Registrar, Inc.</td>
</tr>
<tr class="odd">
<td>DNSSEC</td>
<td>signedDelegation</td>
</tr>
<tr class="even">
<td>Name Servers</td>
<td><p>CODY.NS.CLOUDFLARE.COM</p>
<p>JILL.NS.CLOUDFLARE.COM</p></td>
</tr>
</tbody>
</table>

This isn't enough to mount an attack, but it is essential data that can be useful down the line.
Introduction:

We can consider WHOIS as searching the yellow pages for domain names. It is a TCP protocol that listens on port 43 - we can use WHOIS to look for databases that contain domain names, IP address and automated systems. It was originally created during APANET era.

The **WHOIS domain lookups** enable us to retrieve information about domain names of an already registered domain - **ICANN** requires that requires people who own domains to enter the **holder's information, domains creation, dates and other info.**

*Basically, the WHOIS database has all searchable domains currently registered worldwide.*

Performing WHOIS lookups:

Whilst there does exist web-based WHOIS tools (whois.domaintools.com), you will get cancer using them, it is better to command line tools because it gives us more control over our queries. **On Linux we can use WHOIS command line utility and on Windows we can use Sysinternals WHOIS.**

Examples:

Linux:
![image1](../../../../_resources/image1-150.png)

Windows:
![image2](../../../../_resources/image2-121.png)

