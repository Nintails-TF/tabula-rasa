---
title: 'GET:'
updated: 2023-01-20T20:00:44.0000000+00:00
created: 2023-01-20T19:13:06.0000000+00:00
---

HTTP Basic Auth:

When we visit log in pages and they prompt us for a username and a password. Normally a **POST** request is used to authenticate credentials.

But, you can also encounter **basic HTTP authentication**, which is handled directly by the webserver to protect a specific page/directory, without directly interacting with the web app.

When we try to check response headers:
![image1](../../../../_resources/image1-96.png)

We get **access denied**. This confirms that **basic HTTP auth** is being used. To bypass this we need to input credentials, in this case **admin:admin** using the -u flag in cURL:
![image2](../../../../_resources/image2-77.png)

Furthermore, we can also use the following syntax to deal with **basic HTTP auth:**
![image3](../../../../_resources/image3-65.png)

GET Parameters:

Once we are authenticated, we can use a **City search** feature, so we can search a term and get a list of matching cities. The page may be accessing a remote resource to display the page.

We can use DevTools and look at the network (CTRL+SHIFT+E) tab to check the requests. We can also remove any previous requests using the **trash icon.**

We can see a search.php request that is handling our input, with the parameter **search=le.** This helps us understand that the search function request another page for the results.

***We can now send requests directly to search.php to give us full search results, it will return them in a API style format (JSON) without using a nice HTML layout.***

cURL with GET parameters:

We are also able to send GET requests with cURL, we can use the same URL as a normal browser, but dev tools allows to right click any request and **Copy \> Copy as cURL:**
![image4](../../../../_resources/image4-56.png)
*(Note that the copied command contains **ALL** headers used in the HTTP request. We can remove most of them and only keep the important **authentication headers,** like **Authorization.**)*
HTTP Authorization Header:

Adding the **-v** flag to the cURL command:
![image5](../../../../_resources/image5-43.png)
Shows us the Authorization field:
![image6](../../../../_resources/image6-32.png)

Since **basic HTTP auth** is being used, we see that **Authorization** header to **Basic YMRtaW46…** Which is the base64 encoded value of **admin:admin**. If we were using modern authentication (**JWT**) The **Authorization** would be of type **Bearer** and would have a longer encrypted token.

We can also manually set the **Authorization,** without supplying creds, to see if we can access the page. We can use the **-H** flag and we can use the same value above the HTTP request. We can also add the **-H** multiple times to specify many headers:
![image7](../../../../_resources/image7-26.png)

This also gives us access to the page. *However;* most modern web apps use login forms with back-end scripting language (PHP) which uses **POST**, requests to authenticate the users and then returns a cookie to maintain their authentication.

Console Requests:

We can repeat the same request in the dev tools console, we do this via **Copy \> Copy as Fetch**. Which allows us to copy and HTTP request and then fetch it inside the JS console:
![image8](../../../../_resources/image8-22.png)

curl '<http://165.227.231.233:31413/>' -H 'Authorization: Basic YWRtaW46YWRtaW4='
