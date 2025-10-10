---
title: 'Hydra Modules:'
updated: 2023-08-16T13:56:29.0000000+01:00
created: 2023-08-16T11:18:49.0000000+01:00
---

Creating our payload:

So now we know that we need:
1.  *A URL Path towards the login form*
2.  *POST parameters for username and password*
3.  *A failed or successful login string - this tells hydra if we are logged in or not.*

Our formatted command should look like this:
![image1](../../../../_resources/image1-183.png)

Fail/Success String:

For **hydra** to distinguish between a failed or successful login we need to specify the source code that we are using to log in. *We can specify two different types of analysis to act as Boolean flags:*
![image2](../../../../_resources/image2-150.png)

**For Fail strings,** hydra will keep looking until the string is **not found in the response.**
**For Success strings,** hydra will keep looking until the string is **found in the response.**

In general, we can usually look at error messages - **Invalid log-in details** - if we don't receive any error messages this can make the process more challenging.

So to log into a form we need to pick some kind of flag which will **only show in the login page and not afterwards**.

A good item to pick for the flag would be the **login button** or the **password field.** The login button is slightly more reliable. So we now need to look at the source code of the admin panel and locate the **login button:**
![image3](../../../../_resources/image3-116.png)

We don't need to give the whole login string, but just **\<form name='login'** will be distinct enough to not exist after a successful login,

**This gives us the final string for our http-post-form:**
![image4](../../../../_resources/image4-92.png)

Introduction:

Since we have found an login on an admin panel, we will want to gain access to this - **without making lots of network traffic** - if we gain access to the admin panel we can manage the server, its configuration and services.

Admin panels also can have plugins or features that enable us to have a shell directly into the OS, like the **b374k shell.**

Login.php:

To avoid sending large amounts of network traffic we can simply try the top 10 most popular admin creds - like **admin:admin**

If we don't get access, we can resort to different tactics, a more widespread method like **password spraying** - in which we use already found, guessed or decrypted passwords across many different accounts.

Hydra Brute Forcing Forms:

Using **hydra -h** we can see what kind of services hydra supports:
![image5](../../../../_resources/image5-72.png)

In our case, we only care about the **http modules:**
1.  Http\[s\]-{head\|get\|post}
2.  Http\[s\]-post-form

The first http module is used for **basic HTTP authentication** and the 2nd module is used for login forms like **php** or **aspx** forms.

Since in our admin panel we are dealing with **login.php** we should try the 2nd method. Now, we need to determine if the web app is using a **POST** or **GET** form. We can test it by logging in and looking at the URL - **or via looking at our web proxy -** Generally, if we see any input of our login in the URL, we know that we are dealing with a **GET** form, If we see nothing - then we are dealing with **POST.**

We can then use the **-U** flag to see the required parameters:
![image6](../../../../_resources/image6-49.png)
