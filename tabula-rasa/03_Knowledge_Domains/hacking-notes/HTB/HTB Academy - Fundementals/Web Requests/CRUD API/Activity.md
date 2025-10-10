---
title: 'Activity:'
updated: 2023-01-22T13:06:13.0000000+00:00
created: 2023-01-22T12:46:24.0000000+00:00
---

![image1](../../../../../_resources/image1-101.png)
We can construct an API request, from the notes, this will print all citiesS:

curl '<http://144.126.226.105:32756/api.php/city>'
![image2](../../../../../_resources/image2-82.png)

Now we need to update a cities name to flag, Let's try rename Derby to flag:

Curl -X PUT -d '{"city_name":"flag", "country_name":"Alex"}' -H 'Content-Type: application/json'

We can check if this works:
![image3](../../../../../_resources/image3-69.png)

Deleting cities:

Let's delete Dallas as a city, we can use the following command

Curl -X DELETE '<http://144.126.226.105:32756/api.php/city/Dallas>

We can check if this has worked:
![image4](../../../../../_resources/image4-60.png)

Which it has deleted Dallas.

Getting the flag:

Finally, lets search for a flag:
![image5](../../../../../_resources/image5-46.png)
HTB{crud_4p!\_m4n!pul4t0r}
