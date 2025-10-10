---
title: 'Web Application Layout:'
updated: 2023-04-02T09:10:12.0000000+01:00
created: 2023-02-03T16:56:18.0000000+00:00
---

Introduction:

No two web applications are the same - they have different designs, uses, audiences and are programmed by different devs. It is important to understand how these applications run behind the scenes and how they can be set up within a company's infrastructure.

Web applications have many different layers, but all fall within three categories:

1.  **Web Application Infrastructure**
    1.  *Describes the structure of required components, such as the database, is needed for the web app to function as intended, Since the web application can be set up to run a separate server, it is essential to know which databases the server needs to access.*
2.  **Web Application Components**
    1.  *These are the components that construct a web app - so the UI/UX, Client and Server components*
3.  **Web Application Architecture**
    1.  *This is the relationship between all various web application components.*

Web App Infrastructure:

Web apps use many different setups, we can refer to these as **models**. The most common models are:

1.  **Client-Server**
2.  **One Server**
3.  **Many Servers - One Database**
4.  **Many Servers - Many Databases**

Client server model:

The client server model is the most stereotypical model that we think of when we think about web applications.

![image1](../../../../_resources/image1-103.png)
In this model we have two main components, the client side (browser) which manages the UI that humans see and the components in the back-end, in which the server does the heavy lifting and compiles and interprets the hosting server.

1.  A client visits a website, the server uses a main web application interface (UI).
2.  Once the user clicks on a button, the browser sends a HTTP web request to the server.
3.  The server then interprets this request and performs the necessary tasks to complete the request.
    1.  Logging in the user, adding an item to the shopping cart, etc.
4.  Once the server has the data it sends the information back to the clients browser in the UI in a human readable manner.

**We access the website (web app) then we interact with it by interfacing with the UI to send requests to the server, the server then sends information back to our client.**

Of course we can send requests using tools like BURP or via the terminal to mimic UI requests.

One-server model:

The one server model is a rather outdated and risky model - though it is easy to implement:
![image2](../../../../_resources/image2-84.png)

If any web app is compromised - then the all web application data will be compromised. This is an **all eggs in one basket** approach. If any of the hosted web apps are vulnerable, **the whole web server is vulnerable.**

A double whammy is that if the singular webserver goes down, all hosted web applications cannot be used to be resolved.

Many-servers and One Database model:

This model represents many servers that use a single database - since all servers communicate with a single database server:
![image3](../../../../_resources/image3-70.png)

The advantage of this model is that several web apps can access a single database without needing to sync data between them.

The web apps can be replications of one main app (primary and backup apps) or they can be different web applications that share common data (spire logs for example).

The main **security advantages** of this implementation is that if one webserver is compromised, other web-servers can function. Also if the main **database** is disrupted (via SQL injection or another vulnerability, the web application is not directly affected.

Still there must be an limit of web application access to only data needed to function as intended.
Many Servers and Many Databases Model:

This model is an extension of the **Many servers, one database** model. However, within the database server, each web application's data is hosted in a separate database.

The web application can only access private data and only common data that is shared across web applications. It is also possible to host each web application's database on a separate database server:

![image4](../../../../_resources/image4-61.png)

This design model is widely used since if any web server or database goes offline, there is a backup that can run to reduce downtime as much as possible.

This requires a more complex implementation and often requires tools like load balancers to function. Though this is the **most secure model** in terms of security - since the assets are segmentate and separated.

Alternative models:

There are separate models for web applications such as **serverless web apps** (For example, having your web application run via AWS) and web applications that use **microservices** (only scaling components that are in demand, rather than scaling whole program**.**

**Alternative models will likely be helpful in cloud-based infrastructure such as AWS or Azure.**

Microservices:

We can think of microservices as independent components of the web application, which in most cases are programmed for one task only. For example, an online store we can decompose core tasks into the following components:

- Registration
- Search
- Payments
- Ratings Reviews

These services communicate between each other and the client, we say that the communication is **stateless**, which means that the request and response are independent.

This is because the data is **stored separately** from each **microservice**. Microservices are often used in a **service-oriented architecture (SOA)**. In which collections of microservices are used to achieve a single goal - like powering an e-commerce website.

Another key advantage of microservices, is that each can be written in **different programming languages** and they can still interact - this makes scaling up certain features easier and makes it easier to build new features.

Other advantages include:

- Agility
- Flexible scaling
- Easy deployment
- Reusable code
- Resilience

Web Application Components:

Each web applications can have different components, but in general, all components can be broken down into the following:

1.  **Client**
2.  **Server**
    1.  Web-server
    2.  Web application logic
    3.  Database
3.  **Services** (Microservices)
    1.  3rd party integrations
    2.  Web App integrations
4.  **Functions**

There are three main components to a web application, otherwise known as the **Three Tier Architecture**:

1.  **Presentation Layer**
    1.  This layer consists of all components that communicates with the application and system. These can be accessed by the client via the web browser, and are returned via the HTML, JS and CSS requests.
2.  **Application Layer**
    1.  This layer ensures that all clients requests (web requests) are correctly processed. Various criteria are checked such as authorization, privileges and data passed to the client.
3.  **Data Layer**
    1.  The data layer works closely with the application layer to determine exactly where the required data is stored and can be accessed.

An example of a web app, can be described by looking at the ASP.NET core:
![image5](../../../../_resources/image5-47.png)

Serverless Architecture:

Cloud providers like AWS, GCP and Azure now have options to build serverless web applications, in which web apps are run in stateless computing containers (Docker, Kubernetes, etc). This means that the cloud provider can handle all the infrastructure and businesses and just go on their merry way without needing to worry about scaling or maintaining servers.

Conclusion:

Vulnerabilities can present themselves in the fault of its server architecture. For example, a single web app might be secure, but due to a lack of proper access control, certain users can access admin features or sensitive commands without needing privileges.

Understanding server architecture helps you build a map in your mind or enables you to start to understand the systems that are at work and can enable you to move laterally to find more juicy information.

