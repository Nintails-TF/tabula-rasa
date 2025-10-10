---
title: Parameter Fuzzing - POST
updated: 2023-07-30T16:53:24.0000000+01:00
created: 2023-07-30T16:42:08.0000000+01:00
date modified: Monday, May 13th 2024, 11:01:35 pm
---

The main different between POST and GET is that POST requests do not use URL and cannot be simply fuzzed using the **?** Symbol. **POST** requires are passed in the data field within the HTTP request.

*Note that POST only accepts data that has the correct header of "application/x-www-form-urlencoded. So we need to set the **-H flag** to* "-H 'Content-Type: application/x-www-form-urlencoded'".

So to fuzz the **data field** with **ffuf** we need to use the **-d** flag. We also have to add **-X POST** to send **POST** requests. For example:

**ffuf -w /opt/useful/SecLists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u [http://admin.academy.htb:PORT/admin/admin.php](http://admin.academy.htb:PORT/admin/admin.php) -X POST -d 'FUZZ=key'-H 'Content-Type: application/x-www-form-urlencoded'-fs xxx**

We can also use **curl** to see if a **POST** request with the **id** parameter, we can do that with **curl**:

**curl [http://admin.academy.htb:PORT/admin/admin.php](http://admin.academy.htb:PORT/admin/admin.php) -X POST -d 'id=key'-H 'Content-Type: application/x-www-form-urlencoded'**

We receive a method stating we have an invalid id.

