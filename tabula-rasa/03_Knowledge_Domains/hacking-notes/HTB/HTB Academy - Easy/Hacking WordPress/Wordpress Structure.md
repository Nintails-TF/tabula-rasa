---
title: Wordpress Structure
updated: 2023-07-19T17:36:26.0000000+01:00
created: 2023-07-19T16:56:49.0000000+01:00
date modified: Monday, May 13th 2024, 11:05:16 pm
---

Critical Wordpress Files:

The root directory of WordPress contains files that are needed to configure WordPress to function correctly, The most key files are:

- **Index.php**
  - *Is the homepage of Wordpress*
- **License.txt**
  - *Contains useful information such as the version of Wordpress installed*
- **Wp-activate.php**
  - *Used for the email activation process when setting up a new Wordpress site.*
- **Wp-admin**
  - *This folder contains the login page for the admin access and the backend dashboard. Once a user is logged in they can change the site according to their assigned permissions.*
  - *The login page can be located at one of the following paths*
    - ***/wp-admin/login.php***
    - ***/wp-admin/wp-login.php***
    - ***/login.php***
    - ***/wp-login.php***
  - ***This login page can also be renamed to make it harder to find and protect it from automated scanning.***
- **Xmlrpc.php**
  - *Is a file that Wordpress uses to enable data to be transferred using HTTP and encoding it using XML. However, this type of communication has been replaced with the Wordpress REST API.*

Wordpress configuration file:

The **wp-config.php** file contains lots of key information used by Wordpress to connect to the database. Such as:

- Database name
- Database host
- Username and password
- Authentication keys and salts.
- Database table prefix

We can also use this to activate DEBUG mode which can be useful in troubleshooting, we can see below:
![image1](../../../../_resources/image1-121.png)
![image2](../../../../_resources/image2-98.png)

Default File Structure:

Wordpress can be installed on all hosts (Linux, MacOS and Windows). We will focus on the **LAMP** stack since it is very popular (Linux, Apache, MySQL and PHP). After installing Wordpress all of its supporting files can be found in the Webroot of **/var/www/html.**

Below is the default file structure of a default Wordpress install - it gives us the key files and subdirectories for the website to function properly.

![image3](../../../../_resources/image3-79.png)
Key WordPress Directories:

Other directories that are worth looking in are:

- **Wp-content**
  - *This is the main directory where plugins and themes are stored. In particular, **uploads/** is usually where any files are uploaded to the platform.*
  - ***These directories should be carefully enumerated because they can have data that could lead to RCEs or other vulnerabilities.***
  - ![image4](../../../../_resources/image4-64.png)

- **Wp-include**
  - *This is where everything except from admin components and website themes are stored. This includes*
    - *Certificates*
    - *Fonts*
    - *JS files*
    - *Widgets*
  - *Again it is worthwhile to look here for insecure widgets or JS files.*
  - ![image5](../../../../_resources/image5-50.png)

