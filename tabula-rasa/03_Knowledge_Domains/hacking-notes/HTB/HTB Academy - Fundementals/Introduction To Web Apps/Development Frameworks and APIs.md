---
title: 'Development Frameworks and APIs:'
updated: 2023-07-18T19:02:39.0000000+01:00
created: 2023-07-18T09:52:51.0000000+01:00
---

Introduction:

In addition to web servers, we also have web development frameworks that help is creating core application files and functionality. With web apps becoming more complicated it is hard to create a sophisticated application from scratch, so most popular website are developed using web frameworks.

Simple functionality like user registration and login can be handled by these web frameworks, the most common web development frameworks are:

- **Laravel (PHP)**
  - Laravel is generally used by smaller startups and companies, since it is powerful and simple to develop for.
- **Express (Node.JS)**
  - Express is used by PayPal, Yahoo, Uber, IBM and Myspace.
- **Django (Python)**
  - Django is used by Google, YouTube, Instagram, Mozilla and Pinterest.
- **Rails (Ruby)**
  - Rails is used by GitHub, Hulu, Twitch, Airbnb and Twitter in the past.

*It is important to realise that most popular websites use **multiple** frameworks. Rather than just sticking to one.*

APIs:

An important aspect of back end web app development is the use of **Web APIs** and **HTTP request parameters** to connect the front end and back end to be able to send data back and forth between the front and back end components.

Since the front-end needs to communicate with the back end to ask for certain data, we use APIs to achieve this. In which the front end sends an request using an API and the back-end processes these and sends back the necessary output.

Query Parameters:

We generally use **GET** and **POST** to send request parameters. We do this since the front end may need to specify certain values for parameters to be used within the back end components. i.e. what kind of fruit are we searching for?

So for example within a **search.php** file, we would take an **item** parameter that specifies the item to be searched for. Our method of searching depends on our PHP method:

**GET - Uses the URL, e.g.** *'/search.php?item=apples',*
**POST -** Uses post parameters at the bottom of a POST HTTP request.

e.g.
POST/search.php HTTP/1.1
item=apples

We can use query parameters to receive various kinds of inputs, for other scenarios web APIs may be much quicker and more efficient to use.

Web APIs:

An API (Application Programming Interface) is an interface within an application which specifies how the web app can interact with other applications, it is what allows us to gain access to the back end. APIs are frequently used within many areas of software development and Web APIs generally use the HTTP protocol.

A weather application for example may have a certain API call to return the current weather for a specific capital city and then would return the current details about the weather in **JSON** format. Another example would be the twitter API which allows us to retrieve tweets from certain accounts in either **JSON** or **XML**.

We can even send tweets via Twitters API if we authenticate our account.

SOAP vs REST:

APIs have different standards, the main two you will commonly see in the field are SOAP (Simple Objects Access) which shares data using **XML** and REST (Representational State Transfer) which shares data using **JSON.**

A SOAP request usually looks like the following:
![image1](../../../../_resources/image1-112.png)

SOAP is very helpful in transferring structured data - so whole classes and even binary data and is frequently used in serialized objects of which enables sharing of complex data types between the front and back-end.

SOAP APIs are very good at sharing **stateful objects** - i.e. sharing and changing the current state of the website - which increasingly is more important in modern web and mobile apps.

SOAP is more complex and requires complex requests for short queries like **searching** or **filtering.** This is where **REST** APIs shine.

REST APIs:

REST APIs share data via the URL path (*search/users/1 - finding the user with the id 1)* and normally returns data in the JSON format.

Unlike query parameters REST APIs usually focus on pages that have a single datatype that are passed via the URL path - this makes REST APIs ideal for **search, sort, filter and filtering.**

REST APIs also break web applications into smaller chunks of APIs and use smaller APIs to perform more advanced functions - this makes them modular and scalable.

The front-end components of a web app are usually designed to take the JSON from REST APIs then display them in a form that is readable to the user. Other outputs of REST APIs include XML or even raw data.

![image2](../../../../_resources/image2-91.png)

REST uses various **HTTP methods** to perform different actions:

- **GET** - is a request to retrieve data.
- **POST** - is a request to create data.
- **PUT** - is a request to modify data.
- **DELETE** - is a request to remove data.

