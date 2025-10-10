---
title: Hardening WordPress
updated: 2023-07-22T02:42:45.0000000+01:00
created: 2023-07-22T01:19:25.0000000+01:00
date modified: Monday, May 13th 2024, 11:05:10 pm
---

The best practices to defend a Wordpress website are:

1.  **Perform regular updates**
2.  **Only download trusted themes and plugins**
3.  **Audit your website and remove unused themes and plugins**
4.  **Download security plugins**
5.  **Remove those who aren't using privileges actively.**
6.  **Configure the hardware to limit the attackers abilities.**

Updating Wordpress:

As with any piece of software we want to ensure our software is as up to date as possible to mitigate the chances of attacks. For this reason, it makes sense to automatically update your core word press version.

We do this by modifying the **wp-config.php file**:
![image1](../../../../_resources/image1-137.png)

Managing Themes:

Only make sure you install trusted/official themes, check when downloading a plugin/theme the number of downloads, rating and last update date. Unsupported plugins are usually more likely to be vulnerable.

Also remove outdated plugins and themes that your website doesn't need - **disabling them isn't enough.**

Enhancing Security:

There are Wordpress plugins that can be used to enhance security - either by acting like WAFs, malware scanners, monitoring software, activity auditing and brute force prevention. A few popular WordPress security plugins are:

- **Sucuri Security**
  - Security Activity Auditing
  - File Integrity Monitoring
  - Remote Malware Scanning
  - Blacklist Monitoring.
- **Ithemes Security**
  - Two-Factor Authentication (2FA)
  - WordPress Salts & Security Keys
  - Google reCAPTCHA
  - User Action Logging
- **Word fence Security**
  - *Has a WAF that blocks malicious traffic*
  - *Premium version that provides real-time firewall rules and malware signature updates.*
  - *Premium also has real-time IP blacklisting to block requests from known malicious IPs.*

User Management:

Users are often targeted during attacks because they are seen as the weakest link, the following practices are ideal to implement to increase security:

- Disable default admin user and create accounts with strong usernames and passwords.
- Enable 2FA for all users
- Restrict users uses concept of least privilege
- Occasionally audit users access and rights and remove those who are unused or uneeded anymore.

Configuration Management:

We can configure our Wordpress system to ensure best security practices, i.e.

- Installing plugins that disable user enumerations so attackers cannot gather usernames for password spraying attacks
- Limit login attempts to prevent password brute forcing
- Rename **wp-admin.php** and relocate it - make it non-accessible to the internet or only accessible certain Ips.

