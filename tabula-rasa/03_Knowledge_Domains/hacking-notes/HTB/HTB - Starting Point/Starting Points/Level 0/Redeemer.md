---
title: 'Redeemer:'
updated: 2022-08-24T21:32:08.0000000+01:00
created: 2022-08-01T10:34:23.0000000+01:00
---

Which TCP port is open on the machine?:

*Port 6379 is running on the machine. The default redis port.*

Which service is running on the port that is open on the machine?

*Redis, which is a remote dictionary server. It is an in-memory data structure store. It is a database that is mainly used as a key-value database and is very popular.*

*Typical usages of Redis are session caching, full page caching, message queue apps and leader boards.*

What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database

*Redis is an **in-memory Database** which means that data is kept in main memory (the RAM) of a computer, whilst traditional databases write and retrieve data from disk drives.*

*In memory databases are more efficient as the require less CPU instructions and don't need to save and load to disk.*

Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments.

*In order to interact with the Redis Database we can use the **Redis-cli** command to interact with the database.*

Which flag is used with the Redis command-line utility to specify the hostname?

*We can use various commands to interact with the Redis DB, **-h** lets us specify the hostname, other useful commands are:*
![image1](../../../../../_resources/image1-55.png)

What is the version of the Redis server being used on the target machine?

*The version of Redis is 5.0.7 which is shown both in the Nmap scan and in the info command whilst connected to the DB:*

![image2](../../../../../_resources/image2-41.png)

What is the command used to select the desired database in Redis?:

*We can use the command **Select,** so to get the first index of the database we would use **select 0**.*

How many keys are present inside the database with index 0?:

*We know that by using **KEYS \*** we can get all of the keys of the current DB.*
![image3](../../../../../_resources/image3-34.png)

We are then able to use *GET flag* to get the flag string:

![image4](../../../../../_resources/image4-26.png)

Firstly, we need to check that we can actually connect to the machine and we should test it using the ping command:

![image5](../../../../../_resources/image5-17.png)

Now that we are actually getting responses we know that the machine is up and running. Using nmap we can then take a look at the ports that it is running.

Remember that we can use -sV to probe open ports for service and version info. Now we can use **-p-** which scans EVERY SINGLE PORT (All 65535 of them). Other Nmap port selection commands include:

![image6](../../../../../_resources/image6-10.png)

However, scanning every single port takes forever, so we can just scan the default redis port:
![image7](../../../../../_resources/image7-7.png)

Connecting to a Redis Database:

To connect we need to specify the hostname and portname.

Hostname (ip): 10.129.78.220
Port: 6379

This allows us to connect to the DB:

![image8](../../../../../_resources/image8-5.png)

We can use the command *info* to get details about the server
