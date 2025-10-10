---
title: SQL injection
updated: 2023-01-11T21:53:54.0000000+00:00
created: 2023-01-02T16:29:51.0000000+00:00
date modified: Tuesday, May 21st 2024, 5:02:49 pm
---

Introduction:

**Cheat sheet- <https://portswigger.net/web-security/sql-injection/cheat-sheet>**

A SQL injection (SQLi) is a type of web vulnerability that allows an attacker to interfere with queries that an app makes to a database. This allows an attacker to view sensitive data; such as other users data and application data.

SQL injections may also allow an attacker to modify or delete data, which can disrupt services and cause persistent damages/changes.

SQL injections can also be used to escalate privileges or in a chain of vulnerabilities, so that an attacker can compromise the underlying server/back-end infrastructure or perform DOS (Denial-Of-Service) attacks.

Impact of vulnerability:

A SQL injection can lead to:
- Access to sensitive data
- Reputation damage
- Fines
- A persistent backdoor into an organization.

You have many different types of SQL injections.

**Retrieving hidden data:**

Take for example a shopping application, that when the user clicks on the Gift category, their browser request the URL (Uniform resource locator): <https://insecure-website.com/products?category=Gifts>

The causes the app to make an SQL query to retrieve details about products:
***SELECT \* FROM products WHERE category = 'Gifts' AND released = 1***

This SQL query returns:
- All details (SELECT \*)
- From the products tables (FROM products)
- Where the category is gifts (WHERE category = "Gifts")
- And the product is released (AND released = 1)

As an attacker, what we would want to do, is to manipulate the query so that we can get information on the whole table, potentially on the unreleased products. We can manip the URL like so:
*<https://insecure-website.com/products?category=Gifts'>--*

This results in the query becoming:
***SELECT \* FROM products WHERE category = 'Gifts'--' AND released = 1***

Since a "--" is used as a **comment** in SQL. This will cause the AND statement to not be interpreted, which causes unreleased products to be displayed to the user.

**Extending this example, We can display all items using:**
*<https://insecure-website.com/products?category=Gifts'+OR+1=1>--*

This gives the query:
***SELECT \* FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1***

This returns all items - even those that aren't in Gifts, since if category is "Gifts" or 1=1 (which is always true).

**Subverting Application Logic:**

Giving the example of a log in page that takes a username and a password. If the application using the following query via the following SQL query:

***SELECT \* FROM users WHERE username = 'wiener' AND password = 'bluecheese'***

So if the query finds the corresponding details of a username with creds wiener:bluecheese, then the login is successful.

But as an attacker, we can log in as any user without a password by again using the "--" SQL comment to remove the password check from the SQL statetment. Allowing us to execute the following query:

***SELECT \* FROM users WHERE username = 'administrator'--' AND password = ''***

This will return the username of the admin and log the attacker in as the admin.

**Retrieving Data From Other Database Tables:**

In the event that the user can see the query output via the website/application. The attacker can use a SQL injection to try to retrieve data from other tables within the database. This can be done via using the **UNION** keyword. Which lets you perform multiple SELECT clauses in the SQL query.

For example:

***SELECT name, description FROM products WHERE category = 'Gifts'***

Then an attacker can input:

***' UNION SELECT username, password FROM users--***

This allows the attacker to try and get creds from the *users* table.

An extension on Union SQL injects is here: <https://portswigger.net/web-security/sql-injection/union-attacks> (It has some cool labs in it).

**Examining the database:**

After identifying a SQL injection vulnerability, it is useful to obtain info about the database in question. This allows for further exploitation to occur. You can query the database using the database type, so on **Oracle** DBs you can execute:

***SELECT \* FROM v\$version***

Furthermore, you can determine which database tables exist and which columns they contain. For example, on most databases you can execute the following to find out which tables exist:

***SELECT \* FROM information_schema.tables***

An extension on examining databases is here: <https://portswigger.net/web-security/sql-injection/examining-the-database> (more labs).

