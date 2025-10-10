---
title: 'Databases:'
updated: 2023-07-18T16:51:00.0000000+01:00
created: 2023-07-18T09:06:02.0000000+01:00
---

Introduction:

Web apps use back end databases to store various content and info related to the web application. This can be core assets like images and files, content like posts and updates or user data like usernames and passwords. This allows web applications to easily and quickly access data and serve dynamic content specific to each user.

There are many different types of databases, but most developers are looking for a few main features when choosing a database, mainly:

- **Speed**
  - How fast can we store/receive data?
- **Size**
  - Can we store large amounts of data?
- **Scalability**
  - Can we easily expand the database if our app increases in popularity?
- **Cost**
  - Can we afford it?

Relational SQL DBs:

Relational databases store data in tables, rows and columns - each table has a unique keys - **primary, foreign, compound keys, etc.** Which are used to create relationships between tables.

For example, We can have an **users** table with an id column, which is linked to the posts table using user_id:
![image1](../../../../_resources/image1-111.png)

The benefit of this is that we can access user details for each post without storing all the user details within a post. Of course there are many different ways to link tables together and this is a very simple schema.

(Schema is the relationship between tables in a database.)

Relational databases are good at quickly accessing and retrieving all data about a certain element from all databases. They are very fast and reliable for big and concrete datasets - relational databases also makes data management very efficient.

The most common relational databases include:

1.  **MySQL**
    1.  MySQL is free and open-source and is the most commonly used database in the world.
2.  **MSSQL**
    1.  Microsoft's implementation of relational databases - it is commonly used in Windows servers and IIS web servers
3.  **Oracle**
    1.  Oracle is very fast and reliable and is commonly used in big corporations and Is combined with innovative database solutions to increase speed - but it is very expensive even for big corporations.
4.  **PostgreSQL**
    1.  A free and open source relational databases that is very modular and can be extended and enhanced without changing the initial database design.

Non-relational databases:

Non-relational databases do not use tables, rows, columns, schemas and primary keys. **NoSQL** databases stores data in various storage models depending on the type of data.

Due to the lack of defined structure within these NoSQL databases they are very **flexible and scalable** and are best used when the data inputted is not well defined.

There are 4 common storage models for **NoSQL** databases:

- **Key-Value**
- **Document-based**
- **Wide-Column**
- **Graph**

The **Key-value** model usually stores data in **JSON** or **XML,** and has a key for each pair storing all of its data as its value:
![image2](../../../../_resources/image2-90.png)

We can interpret this using **JSON** as:
![image3](../../../../_resources/image3-75.png)

The **document-based** model stores data in complex **JSON** objects with each object having meta-data whilst data is stored like the key-value model.

The most popular **NoSQL** databases are:

1.  **MongoDB**
    1.  This is the most common NoSQL database, it is free and open source and uses the **document-based** model and stores objects in JSON.
2.  **Elasticsearch**
    1.  This is another free and open source database project. It is optimized for large datasets and is very fast and efficient in searching for data.
3.  **Apache Cassandra**
    1.  Also free and open-source, it is good at scaling and can handle false values well.

Implementation in web apps:

Most modern web development languages make it simple to utilize various database types - but first a database must be installed on the back-end and once it is running web apps can start using it to store and retrieve data.

For instance, in **PHP** once we configure a **MySQL** database, we can connect via:
***\$conn = new mysqli("localhost", "user", "pass");***

We can create a new database using:
***\$sql = "CREATE DATABASE database1";***
***\$conn-\>query(\$sql)***

We then can execute SQL queries by using MySQL syntax:
***\$conn = new mysqli("localhost", "user", "pass", "database1");***
***\$query = "select \* from table_1";***
***\$result = \$conn-\>query(\$query);***

Web apps usually use **user-input** when retrieving data, so when a user performs a search functions for other users, this is **passed into the web application** and the query is performed:
***\$searchInput = \$\_POST\['findUser'\];***
***\$query = "select \* from users where name like '%\$searchInput%'";***
***\$result = \$conn-\>query(\$query);***

The website then will give the response to the client:
***while(\$row = \$result-\>fetch_assoc() ){***
***echo \$row\["name"\]."\<br\>";***
***}***

The danger is that a user can craft an erroneous query to execute a query that the developers didn't intend to be possible and perform a **SQL Injection attack.**
