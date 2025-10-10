---
title: 'CRUD API:'
updated: 2023-01-22T12:58:03.0000000+00:00
created: 2023-01-21T20:50:37.0000000+00:00
---

Introduction:

We saw example of a how city search web applications use PHP parameters to search for a city name. We can also interact with **APIs** to perform the same thing and cut out the middleman of interacting by interacting with the **API endpoint.**

APIs:

There are many types of API that are used to interact with a database, such that we can specify a requested table and row using our API query, then we can use a HTTP method to perform the operation needed.

So we can use the **api.php** endpoint, to update the **city** table in the database:
![image1](../../../../_resources/image1-100.png)

CRUD:
We can use various HTTP methods to perform different operations on that row, there are 4 main HTTP operations that corollate to the 4 main types of database operations:
![image2](../../../../_resources/image2-81.png)

These four operations are mainly linked to the commonly known CRUD APIs, the same principle is used in REST APIs and other APIs. Not all of them work the same and there are limits on what each type of user can access.

Reading:

Often the first thing we want to do is to read data from the API:
![image3](../../../../_resources/image3-68.png)

We can see that the result as a JSON string. We can **pipe** the output to the **jq** utility. Which will format it properly, We can also use the **-s** flag:
![image4](../../../../_resources/image4-59.png)

We can then change the search term and get all matching results:
![image5](../../../../_resources/image5-45.png)

Also you can pass an empty string to see **all results:**
![image6](../../../../_resources/image6-34.png)

Create:

To add a new entry, we can use a **HTTP POST request**. We can POST any JSON data and it will be added to the table. But to do this we also need to set the **Content-Type** header to **JSON:**

*curl-X POST -d '{"city_name":"HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'*

To check the content of the city we can perform a read for our data we inputted:
![image7](../../../../_resources/image7-28.png)
(*Note that you can do the same thing using the Fetch POST - copy \> copy as fetch - using the JS console)*

Update:

Now that we know how to read and write through APIs, we can use **PUT** to update API entries and modify their details.

*(The **PATCH** method way also be used to update API entries instead of **PUT.** To be exact, we use **PATCH** to partially update an entry, whilst **PUT** is used to update the whole entry. We can also use the HTTP **OPTIONS** method to see which of the two is accepted by the server.)*

Using **PUT** is quite similar to **POST** in this case, We need to specify the name of the entity we want to edit in the URL, So we have to do specify the **city** name in the URL, to change the request method to **PUT**, and provide the JSON data we did with POST:

Curl -X PUT -d '{"city_name":"New_HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'

Again, we can check that the city of London has been replaced with the HTB city:
![image8](../../../../_resources/image8-24.png)

*(In some APIs, the **update** operation may be used to create new entries as well. For example, if an entry named **london** doesn't exist. **Update** would create a new entry with the details we pass in.)*

Delete:

Deletion isn't too complicated, to delete an entry we use:
![image9](../../../../_resources/image9-20.png)
Then we can confirm that the entry is deleted:
![image10](../../../../_resources/image10-15.png)

Privileges:

In the real world, all 4 CRUD operations would likely not be possible. Such actions would normally be a vulnerability, if anyone can modify or delete an entry. Each user would have certain privileges on what they can and can't do. Be it **reading, writing (**adding, modifying or deleting data).

To authenticated to an API, we would need to pass a cookie or an authorization header (JWT).
