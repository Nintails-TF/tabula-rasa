---
date created: Friday, December 5th 2025, 10:58:48 am
date modified: Saturday, December 13th 2025, 3:12:27 pm
---

# Unit 1 - Approaches to Software Development:


# 1. Introduction:

Software development within this module is presented as an engineering problem. In that we care about the question of: **How do we build quality software?** This is achieved by devoting energy to product (What are we building?) and process (How are we building it?).

Successful software projects must:
1. Meet requirements and satisfy user expectations.
2. Resolve conflicting needs of a diverse pool of users.
3. Be developed within deadlines and on budget.
4. Be resilient or adaptive to change over the course of its operational lifetime.
5. Ensure that the system is high-quality.

***

# 2. Software and Software Engineering:

Once a software system is built, the systems don't remain static - so maintaining and updating software is key. 
## 2.1. What is a System?:

The word [[../Glossary#^sys-def|System]] is often thrown around frequently within daily life. It's derived from the Greek word meaning "to set up". 

Systems are defined by their organisation and connectivity. A network of phones, switches, and wires would be a network. But a pile of old telephones, wires, and switching wouldn't be; as the **organisation** and **connections** have been lost.

Systems are then greater than the sum of their parts. Properties of a system can't be deduced by looking or analysing a single component (or even all of it's components, it's really the flow of the **connection** and **organisation** which is the core of a system).

In this way, whilst predictions about system performance can be made, we cannot know for certain until the system is active.

The assembly of components that forms a system, results in a transformational process. This process works on inputs, carries out a transformation, and produces outputs towards a goal. 

If you view the human body as a system:
1. **Foundation/Components**: bones, organs, skin, etc.
2. **Inputs**: oxygen, food, energy, etc.
3. **Transformation**: metabolic processes, circulation, cellular respiration
4. **Output**: sustaining life, movement, growth

This module is about: **Software Development.** Meaning we don't care about how or where the hardware is installed, but we look at technical components within programs and how they fit into other social settings, such as [[../Glossary#^SoTech-def|Sociotechnical Systems]].

In honing in on software, we'll be ignoring many other components that are required to produce a quality system [[../../TM353 - IT systems planning for success/Block 1/Part 1 - Successful IT Systems|(See TM353)]]. Media, managers, and companies are heavily invested in either praising and rewarding failures, or covering and denigrating failures.

#### Example 2:
*The [Ariane 5 unmanned rocket](https://en.wikipedia.org/wiki/Ariane_flight_V88)failed upon launch due to a software problem, which caused an overflow software exception during flight, wasting $370M as the rocket disintegrated.*

Systems are often a *personal ordering of reality*, or a result of viewing some level of logic/order/reason within an environment or piece/group of data. This means that systems can be many different types of things depending on **viewpoint** of who is studying/using it and why.

#### Example 3:
*A mobile telecommunications system, is a method of communication for users. For engineers it's a technical system to maintain. For executives it's a business to manage, and for router designers it's how can they make a quality sub-system within this paradigm.*

Example 3, highlights how the **system boundary** differs from each viewpoint, you can divide a system up into components that you care about (software) and consider the outside factors as environmental (hardware).

The [[../Glossary#^domain-def|Domain]] of a system would be the particular area of interest that we are looking to develop/enhance or maintain.
#### Example 4:
*A hospital has a domain for software that asks how to join together a series of patient-monitoring systems with databases that mange medical records and appointments, which then builds a larger system with a different scope.*

#### SAQ 1:

Example 4, illustrates how a set of components can be combined into a larger system. What would the answer to the following questions be?:

1. Suggest and additional component that might be possible with the combined system, that would not have been possible with the components alone.
	1. *Integration and updates with real time data, so if patients are being monitored, their health conditions and records would be able to be updated seamlessly. You could generate new insights by looking at data to create Predictive Diagnostics and Early Warning Systems to flag higher risk patients.*
2. What can you say about the boundary of the original system and the combined system?
	1. *The boundary of the original system is more simple, as you consider what actions that the component takes, the newer system has more fuzzy boundary, as the integration of parts leads to it being difficult to say where the system stops and starts.*

## 2.2. The Nature of Software:

Software is often referred to as being invisible or intangible. Hence, it is perceived differently than physical applications which break and wear down over time. This can lead to unrealistic expectations of software or unrealistic budgets/timeframes.

This then contributes to the myth that software is simple and accommodating change is easy. There are three main characteristics that impact development and the likelihood of errors:

- **Malleability**
	- *Software is easy to change, programmers often tweak and improve code. This creates pressure to constantly edit and change code, each change adds another chance for failure.* 
- **Complexity**
	- *Software is often complex, and the rate of errors arise as a program becomes more logically complex. This complexity is easy to recognise, but hard to define. Basically if something requires lots of explanation, then it tends to be complex.*
- **Size**
	- *It is likely that more errors will arise in larger projects, than with smaller ones.*

#### SAQ 2:

Explain why errors could occur in relation to these three factors:
- **Malleability**
	- *Changes can occur without proper consideration of the knock on consequences. This can result in scope creep, outdated documentation, and a lack of understanding. If change isn't implemented in an orderly fashion.*
- **Complexity**
	- *The more moving parts, the greater the chance that a small bug or error can either snowball or that an innocuous change can harm another part within the system.*
- **Size**
	- *The more lines of code, the greater the chance of errors is.*

## 2.3. Characteristics of a Software System:

There are two main questions to consider when addressing software systems:
1. What characteristics should we be looking for in a software system so that we can develop one that meets the needs of all users?
2. What attributes of a software system have to be high quality for a powerful system?

Software is typically developed due to an identified need. For instance:
- **Business/Corporate**
    - Clients/Customers want software to solve a problem.
- **Self-development**
    - You develop a solution to a problem that you are having.

Software can be made without a specific client in mind, in the hope that the work speaks for itself or that people will use the solution in the future. The contract between a customer and developer includes the software specifications; what it must be able to do and within what environment it will work.

We categorise software as **useful** if it meets the needs of its users. To users, software is represented using the **user-interface** if the UI is clunky, unresponsive, or hard to use, then users cannot access the full power of said software, then the [[../Glossary#^usability-def|Usability]] of the software would be lacking.

We expect that software systems are [[../Glossary#^reliability-def|Reliable]], in that errors are minimised and operations run smoothly, otherwise users will be unable to actually access and perform expected tasks.

A software system must also be [[../Glossary#^flexibility-def|Flexible]], as the needs of the users will change and adapt over time, new requirements will arise as the system is developed and grows, and specifications can be overlooked or missed during the analysis phase. Flexibility is key as it also enables us to fix errors when needed.

Another key characteristic is [[../Glossary#^availability-def|Availability]], no matter how usable or useful a piece of software is, if it cannot be accessed or used within the customers target environment with the services that they use, it is useless.

A business requirement that also plays an important role is [[../Glossary#^affordability-def|Affordability]], developers must be able delivery software on budget and customers must be offered a price in which they are willing to buy and maintain the software for.

Additionally, a developer team requires skills and manpower to get the project done, the team behind a technical lead or developer contract often dictates the success or failure of a project.

In essence, we are concerned in creating software systems that meet these system requirements, we need useful software systems and the tools to be able to define them, produce a design solution, and then execute upon the plan.

---

#### SAQ 3:

**A):** What is the defining quality of a good software system and what are it's main characteristics?

*Good software is a system that primarily fits user needs first. Other key requirements include: usability, reliability, flexibility, availability, and affordability.*

**B):** How might greater flexibility make a software system more affordable over its whole life?

*User needs and system requirements evolve over time, if it takes less time and energy to modify an existing solution, developers or consultants need to be paid less or billed less hours to rectify new changes.*

**C):** Give two reasons why delivered software systems might not meet its users needs?

*Software systems can often miss user needs for a few reasons. This can occur because users needs may not be captured during development or users needs or behaviour changes over time.*

## 2.4. Maintainability and other Software Problems:

A software system should meet the aforementioned requirements, in order to achieve user and stakeholder satisfaction. An often overlooked portion of software development is [[../Glossary#^maintainability-def|Maintainability]].

In order for maintainability to be achieved, a few different factors and actions have to be achieved. This list is by no means exhaustive, but is a strong starting point:

1. Clearly written documentation about the function of the software system.
2. Well written code with comments and explanations.
	1. This helps as any new developers joining the team, or when a developer leaves the project other members can be clued in effectively.
	2. It reduces knowledge silos.
3. Ensure system flexibility, if a developer programs in a way that increases flexibility this saves money and time down the line.
	1. Modular code, following OOP paradigm, etc.
	2. Makes it so that the cost of a system doesn't increase as rapidly over time.

### 2.4.1. Legacy Systems:

A significant problem that relates to maintainability are systems that have been operation for a very long time; e.g. [[../Glossary#^legacy-systems-def|Legacy Systems]]. If it continues to meet user needs, then the system will cease to be developed or touched and there will be little motivation to change (Don't fix what isn't broken).

This is especially the case with system critical services or sensitive processes such as:

1. **COBOL-based banking systems** - The majority of ATMs and major transactions rely on COBOL code written in the 1970s-1980s. Major banks are very hesitant to change these systems since they have worked reliably over time.
2. **Air traffic control systems** - ERAM (En Route Automation Modernisation) took decades and billions of dollars to partially modernise, maintaining 24/7 safety-critical operations is very complex.
3. **Benefit systems** - The COBOL mainframes from the 1970s return. Personal data of millions of people are handled by these systems, making the replacement of systems risky as both a technical move and a political one.
4. **Hospital systems** - Patient records and digital data use systems built in the early 1990s-2000s since they contain patient data and integrate with medical systems, downtime or data loss could result on patient care and safety.

The organisations that need updates the most, cost the most and require solving decades of technical debt to solve. So patching and maintaining is easier in the short-term, rather than rebuilding from scratch.

Legacy systems in general have the following characteristics:
- Old
- Large
- Developed using old programming languages
- Are business critical
- Changed a number of times since their inception
- Difficult to understand due to a lack of internal documentation, or a lack of experience within the group responsible for them.
    - Many of the people who originally made these systems have either moved on, retired, or died.

Because of these factors, legacy systems become difficult to maintain. *But why can't businesses just bite the bullet and move to new systems?*

The change from old to new introduces risk and implications. Changing software may not only result in an organisation needing technical changes, but to introduce new training to teach employees to operate the system. Certain industries may need to completely overhaul their structure.

Maintaining business services is also an important consideration - A bank does not want to stop processing payments - so the changeover process introduces unknown risk and downtimes. Whereas the legacy system is known risk.

Human psychology also plays a key factor within legacy systems. Staff turnover can ensure that nobody who worked on the legacy system is still around, even if they are still around they may refuse to work on it. When faced with a choice of dealing with some old and archaic mess, most developers choose to move to new fresh projects.

There is also the idea, that the new modern solutions eventually become legacy systems that must be maintained - or that **Today's solutions are tomorrow's problems.** This highlights how **maintainability** and **flexibility** within software design is critical.
### 2.4.2. Unsuccessful Software Systems:

#### Example 6:
1992, London ambulance services commissioned a computer-aided dispatch (CAD) to get ambulances and crews to response to incidents better. It was intended to replace the old paper-based approach. However; there were two notable failures of this new system in November of 1992 that resulted in delays.

The final report of the system failures identified a number of major management problems, a technical audit revealed that the CAD system was incomplete and not fully tested. It's ability to deal with heavy loads nor a backup service had been tested. Finally, there was outstanding problems with the accuracy of the information needed to initiate a dispatch.

The truth of the matter is that successful systems are often not reported. But system failures especially in systems that relate to life and death, e.g. ambulance services, get big publicity. London ambulance services had software that was lacking in usefulness, usability, reliability, and availability.

This paints a pessimistic view, but many software systems do work, however the rate in which systems and software is evolving is lightning fast, so understanding best practicing when developing software is key.

#### SAQ 4:

**A)** Suggest a means of measuring the maintainability of a software system?
*We can suggest that there are a few main qualities that define **maintainability**:*
1. The speed in which developers can locate and make changes.
2. The effort needed to locate and fix bugs.
3. The effort needed to adapt and change the software to meet users changing needs.

**B)** What can be learned from legacy systems about developing good software systems?
*Legacy systems often can start off as being sound products at the moment in time, but as changes occur over time, especially if the changes aren't documented or understood clearly, the software system becomes more challenging. Legacy systems teach the importance of clear documentation, standards, and long term and flexibility.*

You can think of flexibility as resource, certain changes can degrade future flexibility, where as other changes are neutral or compound flexibility.

**C) Suggest a reason why legacy systems will always be a problem?**
*As software is malleable, it is easy to change. Think of a blacksmith forming metal, there is only a limit in the amount of times that it can be heated, cooled, and moulded, before it becomes brittle and liable to failure.*

Eventually legacy systems become too brittle and fragile to maintain. Then replacement is the only option.

## 2.5. Divide and Conquer:

As computing technology has evolved, we have had the ability and capability to build larger and more complex systems. To facilitate this, software systems themselves have become more complex and larger.

However; we as humans can only understand so many components working together at once, in order to cope with complex or tricky problems the technique of **[[../../../Security/Glossary#^decomp-def|Decomposition]]** can be used.

This involves breaking down a problem into smaller and smaller parts, by looking for patterns within software and identifying smaller sub-systems, these are often referred to as **[[../../../Security/Glossary#^modules-def|Modules]].** These modules are frequently sorted into a hierarchy. (Parent/Child, etc.).

Decomposition, also enables groups of developers and programmers to work together better, as certain people/groups can be responsible for certain tasks or features that they are skilled at or that need completed.

Individuals can still build small software systems well, as a person can understand and grasp the system and all the problems/solutions present. However; caution must be taken as individuals can engage in **[[../../../Security/Glossary#^HeroProg-def|Heroic Programming]]** where an individual attempts to build a more complex system. This may happen because of a personal interest or because of poor management - that this method may be the only way to produce a meaningful piece of software.

However, complex systems like air traffic control are beyond the scope of a single individual, in this case a team is required. The development of these critical systems requires not only strong management, but well defined processes and playbooks.

This ensures that the software system is: *useful, useable, reliable, flexible, available, and affordable.* This results in particular individuals being specialised at handling certain different development activities (Frontend, Backend, Fullstack, Mobile, Embedded, DevOps, SRE, Cloud, DB, App security, Data engineering, QA testing, etc.)
### 2.5.1 Problem and Solution:

As we divide one larger problem into a sub-set of smaller problems, we may expect to reach a level in which we can capture, understand, and describe each sub-problem. However; this isn't always possible due to two key issues:

1. How do we know if the sub-problems are easier to solve than the main problem?
2. How do we know that all our sub-problems will slot back together to solve the main problem?

Often the key in finding solutions to problems and sub-problems is experience and knowledge. Another technique to develop a powerful design or program is the idea of **[[../../../Security/Glossary#^ProbDom-def|Problem Domains]].**

As a developer the problems that you face in the world is outside the realm of a computer system, where you attempt to provide a solution as they are connected to real world problems: ![[../../../../03_Reference/Pictures/External Problem comp sys dia.png]]

Importantly, as a developer you shouldn't worry as much about the program code or quality, but that the solution you deliver solves a problem or problems identified by users. Often projects fail not because of technical expertise, but because the problem design or understanding is poor.

#### Example 7:

One technique that can be used to determine if your solution to a problem is high-quality. Is to consider the following: What kinds of complaints would you receive from users if your software did not work properly?

For example, hotel reservation - *If a reservation was made online and a person shows up to reception to find they don't have a reservation, they would go nuts. Similarly if someone booked a room for 6 and turned up and only got a room for one.*

By considering the largest emotional impact that can be cause by your system failing or not working as expected, you can design solutions that meet these edge cases.

### 2.5.2. Modules and Interfaces:

Within software development there is a long history of **[[../../../Security/Glossary#^modularisation-def|Modularisation]]**. Especially when dealing with large and complex systems.

Typical examples are:

- Programs of applications
- Software Libraries
- Classes, in object oriented approaches, like Java.

**[[../../../Security/Glossary#^modules-def|Modules]]** may appear as self-contained elements because they are all parts of a larger whole, but there is always relationships between them that need to be planned for.

#### Example 8:

Software development within manufacturing businesses. We can identify various systems and sub-systems:

1. Customer interaction
2. Production Line
3. Accounting and bookkeeping
4. Deliveries and logistics

We might end up treating these as separate, even though there are connections between them. For instance: A customer orders a good from the business, in which they need to pay for, and then the deliveries department needs to dispatch the goods. Then the production line needs to build and fabricate the product too, along with being tracked and presented to the customer.

The **[[../../../Security/Glossary#^interface-def|Interface]]** of a module is a description of all the external visible operations and what other modules need to know and do to make use of the system in place. But doesn't store details of how the operation would or should occur. (You can also define different interfaces for different customers, as their needs may be different.)

For example: An interface with a bank account, is an **[[../../../Security/Glossary#^encapsulation-def|Encapsulation]]** of what we know or the bank account is structured by.

Module to module communication may require another separate service to function. These required services are called **[[../../../Security/Glossary#^ContextDep-def|Context Dependencies]]**. They are it's interface, include requirements of any what any clients need to meet, and form a **[[../../../Security/Glossary#^ClientContract-def|Contract]]** with clients. Furthermore; this contract defines what the module will and will not do, so clients can be assured if they meet the requirements of the system, that the system will work for them.

Interfaces help developers work more efficiently. As you can follow the documented rules of what another module or subsystem tells you to do, and not understand how it works. Furthermore, you can spend more time figuring out your role and job within the system, you are also less likely to introduce errors.

This enhances flexibility as the interface can be kept whilst the module could be tweaked or swapped if needed.

Finally once, you've understood a system as being set of modules that are well defined and understood, each with its own interface and context dependencies, you can consider if any can be re-used internally or within a different project. This approach is what has been taken with network communication over time, creating the OSI model and different layers of abstraction over time.

**[[../../../Security/Glossary#^abstraction-def|Abstraction]]** is a particular way of viewing a complex problem and to arrive at a decomposed or simpler problem. You group together similar objects, situations, and ignore certain aspects to focus on situations or scenarios that are key without being bogged down. The key task when building a software system, is to figure out the most suitable abstractions for the problem domain.

We can determine if **[[../../../Security/Glossary#^abstraction-def|Abstraction]]** has succeeded if potential software clients do not need to know more about a specific interface. Having a module that automatically converts dates into a specific format is useful, and it doesn't matter to other clients/services that interact with it how it's built or defined.

### 2.5.2. Coupling and Cohesion:

A module of a system depends on another, then it is possible that we may have to change or update a module. A business may change production methods in the way it calculates the payments required for the goods it produces.

Developers not only deal with the nature of each dependency, but the number of dependencies.

The term **[[../../../Security/Glossary#^coupling-def|Coupling]]** is used to explain this, it refers to the degree in which systems are interdependent on each other. Loose coupling means that components are more independent, whilst tight coupling means that components heavily depend on each other. An extreme case can be **[[../../../Security/Glossary#^CircDep-def|Circular Dependencies]]**.

Developers try to build systems that are loosely coupled at first. Good software is designed so that one change doesn't propagate throughout the whole system. Another benefit of loose coupling is that components are easier to replace and reuse.

No matter the level of coupling, if there aren't any records on how modules or components are coupled, then they might need to be checked to ensure that the system operates properly, Example 9, the Y2K scenario explains this:

#### Example 9:

Data handling within old applications has always been a problem. Representation of a year was stored as a number between 0-99. So years weren't stored as 1996, but 96. However, by the 2000s all of these applications had to be checked to ensure that any error didn't occur in the change over from 19th to the 20th century.

A major problem is that different developers and systems used different methods to represent, read, manipulate the variables that are used in the six-figure date format. This increased efforts required in checking these software systems. If there was a consistent way of handling dates, then one approach could of been figured out then replicated by every developer, minimising the damage.

**[[../../../Security/Glossary#^cohesion-def|Cohesion]]** is a way of describing how closely the activities within a single module are related to each other, Cohesion as a general concept can be described as followed: An organisation has departments, these departments have responsibilities that are cohesive with their role (Marketing) or not (general tasks and office work).

Highly cohesive software performs a single task or objective. The saying of: "Do one thing and do it well" is a strong motto to apply when designing software modules.

Low coupling and high cohesion are often competing goals. If every module only does one thing at a low level of abstraction, we need a complex of additionally modules to perform high abstraction tasks that are tightly coupled.

In our hotel example; certain concepts to represent a room to collect and store data about income form certain rooms is one approach. A better solution in this case would be to create a separate function to handle bill or payments, since a hotel often has multiple streams of revenue and placing all income into a single place is more cohesive than having multiple modules handling payments.

#### SAQ 5:

**A)** Why might you consider splitting up a large project into smaller chunks?
*Limit the number of concepts a single person has to understand, enable groups or teams to specialise on certain areas, split tasks into smaller more manageable chunks.*

**B)** How does the complexity of a software system affect the maintenance task?
*Complex software makes it harder to maintain, as the flow of data and dependencies become harder to track and understand when there is complex integration or many moving pieces. A small change can break a system in unexpected ways, especially if there is lacking documentation.*

**C)** What is a module?
*A module is an identifiable part of a software system that is considered separately. We can say that functions in procedural languages and classes in object-orientated languages. Other imports or library functions can be treated as modules too.*

**D)** Why does it help to have low coupling in a software system?
*Low coupling helps as there is only a few dependencies between modules, meaning that changes don't have knock on effects that propagate throughout the system.*

**E)** Give examples of the kinds of information that would be valuable when considering a change to a given module.
*Two kinds of information are key before enacting a change:*
1. *Which modules are children of the module in question? Where will change propagate to?*
2. *What assumptions have been made in parent/child modules? Where does the risk lie?*

**F)** What are the context dependencies of a module? How do they relate to a module's interface?
*Context dependencies are additional services or requirements that must be present within a module-module connection for them to work together. If the child/user meets the context dependencies requirements, then they should be able to operate effectively with the system and vice-versa.*

**G)** What are the benefits of using modules with defined interfaces?
*The main benefit is that you separate the underlying logic and the presentation, this enables developers to only worry about the feedback they are getting form the interface, rather than having to dive into the code of it, developers hence spend more time on less code that they understand better, bugs are easier to find, and modules can be re-used or replaced with greater ease.*

**H)** Why does it help to have high cohesion in the modules of a software system?
*High cohesion helps, as by having interfaces or related modules paired together, they become more reusable in other applications and contexts. Having high cohesion between payment processes in an example of a powerful cohesion.*

**I)** What characteristics should a module display that will help ensure that it is easy and cheap to develop and maintain, and that errors are kept to a minimum?
*We want modules to have low coupling and high cohesion. This shows we've built a well-designed module: it does one job well (high cohesion), doesn't rely too heavily on other parts (low coupling), and solves a clear user need through a clean interface - either interfacing with developers/users.*

**J)** Why is it important to achieve a balance between coupling and cohesion?
*When constructing a system, you often have a choice between smaller set of loosely coupled, less cohesive modules or a larger set of tightly coupled, more cohesive modules. The former leads to a situation where the codebase is hard to understand, the latter over-abstracts relationships and makes code too complex. Striking a balance is key.*
## 2.6. Architecture:

[[../Glossary#^architecture-def|Architecture]] is associated with the overall structure of a software system, for this module we are using the following definition from [Bass et al (2021):]([Software Architecture in Practice - Len Bass, Paul Clements, Rick Kazman - Google Books](https://books.google.co.uk/books/about/Software_Architecture_in_Practice.html?id=qNnPEAAAQBAJ&redir_esc=y))

> The **Software Architecture** of a system is the set of structured needed to reason about the system, which comprise software elements, relations among them, and properties of both.

Software architecture is important as it tells developers and other stakeholders, about the overall shape of the proposed or realised software system. It provides a framework so that other technologies or techniques can be used to assemble a software system.

Different software architectures work better for different projects and there is a myriad of possible processes. It is one of the earliest decisions that a development that must make, and no matter the size of the system, an approach must be taken.

Architecture is not only important for developers, but for users, customers, maintainers, and other stakeholders, for example:

1. Users may be concerned with how easy the software is to use and learn.
2. Customers may be interested in how much it will cost and when it will be delivered.
3. Software maintainers will be thinking about how flexible and modular the system is, and to understand the repercussions when a change is required for one of the modules.

Hence, the architecture choice often embodies many decisions that will affect that concerns of many stakeholders. It also serves at a platform for different stakeholders to communicate together, as different stakeholders come together and decide how the system will be developed or planned.

Typically, software architects handle these different concerns in order to reach a compromise that suits all parties involved.

#### SAQ 6:

Suggest some similarities and differences between software architecture and building architecture.

*Both jobs are interested in the structure of a system. They want to build a structure or software that meets the needs of customers and the abilities of their team and they act as messengers between different parties.*

*Changing a building once complete is very expensive cost wise, Changing software once complete is cheaper, but you pay for it down the line in terms of time and work invested. Software is more malleable and complex. But as the internal decoration of a building can be changed cheaply and quickly, so can certain aspects of software.*
### 2.6.1. Layers, Components and Services:

A software architecture identifies rules for decomposition and sets assumptions for the modularisation of a software system. A major aspect of architecture is the splitting the software into different components or areas that are used to solve a problem. This approach is handled by using layers. We're going to cover three main types:

[[../../../Security/Glossary#^LayeredArch-def|Layered Architecture]] is often found within computing systems that are distributed. We have a top layer which is UI presented to the user. This layer is most prone to change, as users will request changes here.

The 2nd layer would be the application domain - so how does the code logic function and work to achieve the goal of the user. Unless business needs shift rapidly, these desires will likely not change over time. (e.g. Banking Systems needing payment processing code).

The 3rd layer is the infrastructure layer that includes the various operating systems, dependencies, databases which enables the system to be ported to different platforms or environments.

![[../../../../03_Reference/Pictures/Layered-architecture.png]]

We use the term of [[../../../Security/Glossary#^component-def|Component]] to denote a unit of reuse or replacements within a system. A component could be a class/module that has certain properties that make it reusable or replacable. It may depend on other components as well. These components are well understood, have their own interface and context dependencies.

Standards of building or structuring components can be adopted by other services as to meet the needs of the component. 
![[../../../../03_Reference/Pictures/component-representation.png]]

Another concept related to components is [[../../../Security/Glossary#^services-def|Services]]. A service is a reusable chunk, that is technologically independent, in which it can be invoked or used according to a standard. You can think of SaaS (Software as a Service) such as Google Docs or Gmail, where the standard is a functional web browser.

Do note that technological dependence is required at some point in the chain, i.e. The servers running Gmail will use certain architecture, design, or infrastructure decisions. But the end user of this is not effected by this. (As long as the system works and functions)

A [[../../../Security/Glossary#^SOA-def|Service-Oriented Architecture]] (SOA) is another model of design that is frequently used. Software or programs run within the "cloud". Other concepts that are related would be Platforms as a Service (PaaS) and Infrastructure as a Service (IaaS).

PaaS - Spend more time writing code, rather than managing servers:

- Heroku
- AWS Elastic Beanstalk
- Vercel/Netlify

IaaS - Get computing resources when you need them:

- Amazon EC2
- Google compute engine
- Digital Ocean Droplets
- Linode VPS

#### SAQ 7:

**A)** What are the characteristics of a component? *A component is a module that is considered to be a good level of abstraction for the problem at hand. It should be able to be reused for future projects that either use the same software architecture, or can be easily replaced within the software system. A good component has a well-defined interface, strong cohesion, and low coupling.*

**B)** How does the concept of an architecture contribute to component reuse? *By defining an architecture clearly, you can either reuse the product that you make within a different project as you've built something within a repeatable format, or you can re-use the process and framework again to build a different product.*

**C)** Which form of decomposition might be used in a software architecture? *Decomposition in the form of the three layered architecture (Presentation, App Logic, Infrastructure) is an example of how decomposition can be used, by separating these three components and not linking them together, you make it easier to build or reuse components - as someone building a UI for the user, doesn't have to work with application logic, etc.*

**D)** What are the similarities and differences between components and services? *Both work using interfaces to reach some kind of program functionality. However, components are usually implemented within a specific OOP technology and are business/logically facing. Whereas services are less technologically dependant and are more user-facing.*

## 2.7. Summary of Section:

Software systems are very pervasive in modern society and the systems grow rapidly by the day, we've covered a few key details in software development such as:

- Good software is one which meets the needs of its users.
- The concepts and connections between usefulness, usability, reliability, flexibility, availability, and affordability of software systems.
- Software systems become out of date and transform into legacy systems.
    - What are the issues and solutions to legacy systems?
- Users needs change over time and may be missed during requirements gathering.
- The importance of maintenance.
- The importance of defining a software architecture for projects.
***
# 3. Introduction to Software Development:

In this area, we are introducing the basic activities involved in the development of software, what the life cycle of software is, and what different life cycles are, finally the importance of models as a part of software development will also be covered.

## 3.1. Software Development as an Engineering Activity:

Software development has a great deal in common with engineering, and is defined as:

> 1. The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software; that is, the application of engineering to software.
> 2. The study of approaches as in 1) *(IEEE, 1990)*

This means carrying out and conducting ourselves in this approach when we build software, to consider ourself as engineers. Mainly, taking an approach that matches the IEEE's definition means to focus on building [[../Glossary#^quality-software-def|Quality software]].

The goal of a developer is to build a high-quality software product, to do this we naturally need a well-managed and high-quality development process. The term of *engineering* within software development is associated with a few other features:

1. Developers are concerned with meeting a set of requirements - there is usually an identifiable problem that they can solve.
2. There is a defined process that is used to produce a solution and within that process there are different phases.
3. There are tasks that are done during each phase or in multiple phases that impact the final project. Developers undertake different roles to perform the necessary tasks. (QA, Designer, Tester, Hardware, Software, etc)
4. The quality of the product and the processes by which they are made are both important. You build software in the right way (process), and make the right product (output), to operate in the way it is expected to (testing).
5. Developers use various tools to improve effectiveness and efficiency of tasks performed.
6. There is pre-existing knowledge that developers can use to raise the standards of their software, like the five-factor model, rules for decomposition, standards, etc.
7. There are legal and professional networks which dictate what is commonly accepted or mandated by law.

We are concerned with what tools a developer needs to build a piece of software. Software development is a human activity, where we build systems for a group of people to use. We need to ensure that what we build suits the group we are catering towards, if we build a system that is superior but doesn't meet the needs of users, the system will fail as people will resent, ignore or reject the system.

#### SAQ 8:

Give the characteristics of an engineering approach that supports the argument that software development is an engineering discipline.

Software development - when done at a high standard - follows an engineering approach provided that the following conditions are met:

- Strict requirements are defined as clearly as possible.
- A defined process is used with clear activities, each of which has one identifiable end product.
- Developers can apply skills and experience to the tasks demanded by them
- Validation and verification are essential as building software itself.
- Tools and standards are used.
- Codes of practice and conduct are followed.

## 3.2. The Role of the Development Process:

A **Development Process** is a set of rules that defines how a software development project should be carried out. It includes various activities, which upon completion create more outputs known as [[../Glossary#^deliverables-def|Deliverables]].

The order in which activities are performed are referred to as the **life cycle** or **process model**. Both outline the processes in which the development of a software system will follow, this is where project management and product management occur.

This approach of following a well-defined process is promoted as the best way to meet the diverse needs of users and allows for harmonisation of conflicting demands. However, this approach has also been considered as being too prescriptive, heavy on documentation, and not helping meet the expectations of the customer.

For this reason, it's also important to consider some lighter weight alternatives.

We define [[../Glossary#^customers-def|Customers]] as someone who pays for a software system. Where we classify [[../Glossary#^users-def|Users]] as people who use software on a day-to-day or weekly basis. (Not all users are customers, and all customers are users.)

A successful project development will either meet or exceed the expectations of the [[../Glossary#^customers-def|Customer]]. As previously mentioned software can exist without a customer, and a customer can be found or can see the product then decide to buy it.

### 3.2.1. Software Development Activities:

There are many tasks needed to be done during the software development process, these can be roughly categorised as the following:

- [[../Glossary#^domain-modelling-def|Domain Modelling]]
- [[../Glossary#^requirements-def|Requirements]]
- [[../Glossary#^design-def|Design]]
- [[../Glossary#^implementation-def|Implementation]]
- [[../Glossary#^testing-def|Testing]]

Different methods may sub-dividing the above activities or use different terminology. A specific approach used is the [[../Glossary#^UP-def|Unified Process]] (UP).

You will likely break up most problems into smaller, more manageable chunks, then to deal with the problems one at a time, finally the main challenge is [[../Glossary#^integration-def|Integration]] or bringing all the small solutions back together into a complete project.

This differs from [[../Glossary#^delivery-def|Delivery]] of a system, which refers to the deployment and running of the software system. Though deliver and integration can be combined into a single block depending on the contract. DevOps, a combination of developer and operations, refers to any practices involved with integration and delivery.

Software systems also require [[../Glossary#^maintenance-def|Maintenance]], this enables the software system to evolve over time as well as:

- Correct errors.
- Adapt to a changing environment.
- Introduce enhancements required by the customer.
- Improve software in anticipation of future changes.

The four main activities used to develop software are the following:

1. Analysis
2. [[../Glossary#^design-def|Design]]
3. [[../Glossary#^implementation-def|Implementation]]
4. [[../Glossary#^testing-def|Testing]]

These aren't the only activities involved in developing a good software system, but [[../Glossary#^project-management-def|Project Management]] and [[../Glossary#^quality-management-def|Quality Management]] are also critical, as they are the glue that holds the development process together.

### 3.2.2. Process Models/Life Cycle:

A process model or Life cycle is a description of all the events that a piece of software or system goes through and the sequence in which it happens. The enables us to model our approach by defining how we should place and tackle activities.

The most classical approach would be placing all five activities sequentially: *Requirements, Design, Implementation, Testing, and Maintenance.* This would create the [[../Glossary#^waterfall-def|Waterfall Method]].

The waterfall method has run into a few problems that has been illustrated over time.

1. If you complete the analysis and design stages early on, these can become outdated by the time the project is built or made.
2. Software cannot be used until late in the testing stage, this means that customers and users wait for a long time and can't see or interact with the software development process.
3. Errors that are detected late in development or architectural mistakes are often very difficult or impossible to correct.

For these reasons, the waterfall method is not frequently used within modern software development, the [[../Glossary#^agile-def|Agile]] methodology is generally used more.

Alternative models, like agile - enable for **iteration** meaning that developers can improve outputs or processes from certain modules or activities before moving to the next. You can think of it as tuning a guitar, where you pluck at a string, until you get the desired result.

Iterative processes have the advantage where when the requirements of the project are uncertain, you can start with the work or modules that you know will need built, then as you progress add more requirements in response to either user or customer feedback.

This approach is a **iterative and incremental development** approach. Each loop or iteration cycle is developed within a short - **timeboxed** - period. Where you run through all of the requirements quickly and deliver something, then present it.

Iterative approaches are also benefitable as it allows a company to gather feedback from users or customers to make an informed decision on what to build, update or fix next.

#### SAQ 9:

**A)** What is a development process? *A set of rules that defines how a software development project should be built an carried out, it has various activities and the life-cycle of the software will be indicated based on the order of activities.*

**B)** What should the role of project management be with respect to the deliverables of a development project? *Development of a good software system requires that the project remains on budget and within time. Project managers should identify what deliverables are needed at the current moment in time, and help a development team achieve these goals and remedying any delays.*

**C)** What is the difference between a customer and a user? *A customer is a client who pays for the software system. Whilst a user is a client that engages with the software system. Not are customers are users, and not all users are customers. But you can both be a customer and a user.*

**D)** Suggest a reason why maintenance is a core activity in the development of a good software system? *The needs of users and technology as well as the environment in the world will change over time, meaning that software should be maintained or updated so that the system continues to be helpful.*

**E)** What additional task is needed when the development of a software system is partitioned into a number of requirements. *Integration of each of the slices becomes an important task, before the final or complete version can be produced.*

**F)** What are the assumptions on which thew waterfall model is based on? *The core assumption is that we do not need to revisits tasks that are already completed. It assumes that these tasks have been 100% completed first time, which often isn't true. Or that the endpoint for a task is perfectly defined, which again often isn't the case.*

### 3.2.3. Agile Development:

[[../Glossary#^agile-def|Agile]] development is now the main approach to developing software, to act in an agile manner would be to more light-weight, flexible, faster and simple. The needs of a customer will constantly change until a final state in which the customer is satisfied is reached, so an agile approach seeks to get feedback early and constantly to update what should be getting built and worked on.

- Agile: Meaning to act in accordance to a specific Agile principle.
- agile: meaning to act in accordance to general best practices.

We can use the term **plan-driven development** where you would come up with a method like waterfall to contrast against the agile development approach.

The Agile manifesto has grown in popularity:

- **Individual and interactions** over processes and tools.
- **Working software** over comprehensive documentation.
- **Customer Collaboration** over contract negotiation.
- **Responding to change** over following a plan.

(*As a side note, I'd argue that for certain disciplines you need to focus on the alternative items more than the core items (Documentation is critical for cybersecurity for example). Agile can be misused by project managers and owners, and that this approach of being very customer pleasing works well for software as a business, but isn't reflective fully of all projects. I can see why this has been adopted and why it works, but I can still see problems with this approach.*)

The idea is that whilst agile may not be perfect, nor are traditional methods of developing software, though agile can position developers and companies in a better place.

[[../Glossary#^xp-def|Extreme Programming]] (XP) is one of the most commonly used methods for agile. It defines a few different practices such as:

1. Incremental design
2. Test-first programming
3. Programming in pairs
4. Continuous integration
5. Planning for the week
6. etc.

[[../Glossary#^scrum-def|Scrum]] is also another popular agile approach, as it defines a set of roles, events, artefacts and rules. All events are timeboxed and have well-defined rules, Scrums consist of:

- [[../Glossary#^sprint-def|Sprint]]: A development phase, no longer than a month that as a working deliverable by the end.
- [[../Glossary#^sprint-planning-def|Sprint Planning]]: lasts no more than eight hours.
- [[../Glossary#^daily-scrum-def|Daily Scrum/Stand-up]]: A daily meeting that lasts no longer than 15 minutes, looking at what has been done and planning for the next 24 hours of work.

Agile practices in general are geared towards improve communication and collaboration between developers. These agile approaches have succeeded and been recognised. In particular; the emphasis on people opposed to rigid processes, shorter iterations, and the acceptance that systems change.

Often what happens in real project scenarios is that you don't follow agile completely but you use a sub-set of skills that the organisation and people around you do value.

## 3.3. Choosing an Appropriate Process:

A good software system must fit its intended purpose, hence we need multiple different processes and tools to reach this goal. For example, the following software project of:

- To control a series of gates at level crossings
- To control a manufacturing process for chemicals
- To manage an international stock market
- To manage a super market
- To manage a public lending library
- To administer the activities of a university.
- To manage personal finances
- To control a TV or video recorder
- To play a game on a mobile phone
- To manage electronic funds stored on a smart-card.

Each person who interacts with these systems has a different perspective on what makes a system useful, usable, reliable, flexible, available, and affordable. Hence, we need to take different levels of formality and processes for different clients and people.

### 3.3.1. Choosing the Appropriate Level of Formality:

#### Example 10:

Government legislation requires that software systems must be able to support new administrative functions, when developers are contracted to complete software systems, they are asked to confirm to government standards. One standard such as PRINCE (PRojects In Controlled Environments).

Developers in this case need to show that they are abiding by PRINCE. Developers also need to be able to adopt an approved process for their analysis and design activities, the most common method being SSADM (Structured Software Analysis And Design Methodology).

In essence, there is much more red tape, since the stakes are much higher.

#### Example 11:

In financial businesses being a first mover has a huge advantage in revenue, so there is an incentive to build software quickly to beat you competitors. Every aspect of development is then streamlined to meet this goal.

The aim is to do the simplest things needed that could deliver a working system. So communication overhead is kept to a minimum, developer teams are kept smaller (2-3) who work towards a set of minimal requirements. Ideally producing a small amount of high-quality code.

There still are chances that errors can occur, but because the complexity is much lower there will be fewer tests to engage with.

**Examples 10** and **11** highlight how depending on different situations, you have to adapt your development approach.

The government example of PRINCE highlights the importance of **configuration management** in that all of the nuances of legislation must be met and incorporated into the final solution. In contrast, minimal development time and a narrow scope means that demands are reduced and the speed of development is increased.

In larger projects, a well-defined procedure for controlled develop is necessary. Why? Informal communication isn't enough, a solution is to split teams into their own chunks, like components are. This can work, but leads to a longer or more arduous integration time. Generally this approach is a strong method as you can leverage specialisation of developers.

[[../Glossary#^agile-def|Agile]] development encourages collaborative development, [[../Glossary#^xp-def|XP]] promotes pair programming where code is written in pairs to encourage communication, feedback, and positive feedback.

*(Collaboration is a doubled-edged sword, since if you've got a good pair or system that works together, you gain more than the sum of it's part (Two 100% developers become 250%). But if you are in a dysfunctional collaboration, then the performance of both drop and resentment or social tension can mount)*

At some point, software systems will outgrow their usefulness and developers should consider the expected lifetime of the prospective software. If software has to be delivered quickly, don't rely on a slow and deliberate process.

### 3.3.2. Dealing with Risk:

A software solution to a problem needs to be considered across a broad context of the domain, so that risk can be managed appropriately. For example, in fast-paced industries missing the market window can prove disastrous, as the need for the software dies.

Assessing risks and taking steps towards reducing them, no matter the size of the project; big or small. This is known as [[../Glossary#^risk-management-def|Risk management]].

With a typical project structure the risk is in the requirements. Do you understand requirements? Do you have all of them? Are they changing too quickly? Is there anything you can do to increase your confidence or reduce the risk of project failure. For every decision you make you can lie at any point on the scale from dead wrong to perfectly right, when considering important decisions it is critical to tame and understand risk. As if risks go ignored, poorly answered or unovercome the project will likely fail.

Within an agile approach, this is different. [[../Glossary#^requirements-def|Requirements]] will change and should be under continuous review. By involving customers at each step of the way, you can reduce risk by referring to them and what they want or need. Thus, communication with customers reduces risk, as there is a higher chance you will make a decision they are happy with.

Within any project there is often competing interests between time, budget, and features. The number of desirable features often exceeds the budget or timescale, so choices have to be made. One way of doing this is looking at the risk of what happens when features don't make it to the final project.

If a feature were to be abandoned, what would the overall position of the software project be?

The spiral of risk is a strong example of how we can deal with risk: ![[../../../../03_Reference/Pictures/spiral-of-risk.png]]

As you can see, there are four mains steps:

1. Determine the objectives, the alternatives, and the constraints.
2. Evaluate the objectives and identify and resolve the associated risks.
3. Develop and verify a (partial) solution or project.
4. Reviewing the solution, and plan the activities for the next iteration.

There is no need for a complete solution to be reached at the end of the spiral, but it could be building an MVP. After the MVP is built, perhaps new risks or ideas can surface and then subsequently be resolved. Once your project meets the needs of users, then you can stop.

[[../Glossary#^agile-def|Agile]] development within this approach follows a similar spiral approach, but only more rapidly looping around. These risk driven models help when developing large software systems or when developers have a lack of understanding of the project domain. When there is a large risk of failure, it makes sense to understand the risks more thoroughly.

#### SAQ 10:

**A)** Why might a software development company specialise in a certain kind of customer, such as those in banking or healthcare? *As specialisation means that a software development company can understand the opportunities and risks present within contracted projects, they are in a better place to design high-quality software for their customers. An additional benefit is that the company can use similar development approaches or structures used in previous clients to their new clients.*

**B)** In which of the activities within the agile manifesto would you expect to do your configuration management during a project? *As configuration management is the discipline of managing and controlling change, you would expect maintenance, however quality management would be the activity in which you would perform these tasks. *

**C)** Why are there additional risks when developing large projects? *The chance of failure rises as the scale of a project increases, more errors are likely to be introduced, communication problems also occur with larger teams.*

**D)** What is added to a development process with the introduction of risk management. *Identifying, evaluating and managing risks within each loop of iteration within a project, as that risks are properly contained and controlled.*

## 3.4. Traceability:

Developers first need to figure out what their customers want, then develop a plan to meet the expectations of their customers. If a plan-driven approach is followed, early within development a requirement specification is built to propose what the system needs and what it should od.

Tracing the history of who actually defined the requirements is important, so you can reconstruct who decided on what and who is accountable for the successes or failures within the system.

This [[../Glossary#^traceability-def|Traceability]] is essential for dispute resolution (knowing what was agreed upon during development). For seeing what happens in the project if requirements are modified, deleted, or asserted correctly.

The amount of documentation should mirror the amount of traceability required, nor too much no too little. [[../Glossary#^agile-def|Agile]] approaches tend to favour actually working software over documentation, as documentation can be hard to read and seldom used.

For this reason, if documentation is written it should be easy to understand and have a clear purpose for existing, so it finds use. The level of involvement by external stakeholders also either increases/decreases the amount of documentation.

#### Example 12:

An agile project uses documentation in the form of **user stories** and **tests**. A user story describes a piece of functionality required by a user. Where as a user test is a specific, verifiable condition that proves the software works correctly.

For example:

- User Story:
    - As a [Type of User], I want [Goal/Desire] so that [Benefit/Value].
    - As a customer, I want to filter search result by price, so I can find prices within my budget.
- User Test:
    - Defines how you know that a user story has been completed.
    - Given products with different prices, when a price filter of £0-50 is applied, only products under £50 are displayed.

Changes sometimes also relate to specific code which has been made, you can use tools that manage source code to also track these to preserve usability.

When you are working on a project, there may be [[../Glossary#^deliverables-def|Deliverables]] in the form of documentation. You can view these as explanations that you've understood what a problem is about and to clarify your understanding. This enables you to share what you've done with others, writing and drawing also helps you to view other potential solutions.

Program code is necessary but not sufficient if there is a need to understand the decisions taken. Software development is about producing [[../Glossary#^quality-software-def|Quality software]], the documentation should serve this purpose. Your contract or project definition will also effect the amount of documentation as well; what you should document and how much.

A **Project Notebook** is a disciplined approach to organising thoughts and actions as a software developer. You ca record notes, thoughts, drawing, ideas, and decisions. This can either be on paper as is traditional or digital.

You should carry this notebook wherever you go, as you can note down what your users say about their needs, make some preliminary sketches or models, or even record telephone numbers.

Make a note of the date and the time, then review it regularly to ensure that important questions have been addressed and that the meaningful lessons have been extracted, this relates to [[../Glossary#^traceability-def|Traceability]]:

- Your project notebook can be used as evidence in an enquiry or court of law.
- It helps you review what you have done and how long you took to do some task
- It facilitates learning

### SAQ 11:

**A)** Why is traceability important to the development of software? *Traceability is important as it highlights the timeline of events and who is responsible for what. This enables developers to trace decision making back to design principles/people, so if there are any issues or wins, it's possible to see where the strengths/weaknesses lay.*

**B)** How does documentation contribute to traceability within the development process? *Documentation records the progress from written requirements to functional software. It also can describe how a piece of software was built and how to use it. Documentation aids in traceability as it also highlights what requirements have been completed.*

**C)** Which activities in the Agile development process are most effected by poor documentation? *The whole structure of agile suffers due to poor documentation, as being unable to trace outputs to their inputs makes it impossible to understand the system. Clearly the maintenance and quality management will be the most negatively effected - you run into the problem that legacy systems have earlier on in the life-cycle of a piece of software.*

**D)** For what kind of software system might you minimise or avoid any documentation? *If the software system will only be used a few times or will be discarded. However, there are often times within a company that an ad-hoc solution is developed with the idea of replacing it or building a stronger solution later, but that day doesn't come. So documenting even these smaller projects still can be useful, especially if they are part of a larger integrated system.*

**E)** How would you characterise agile documentation? *Agile documentation differs as it is gathered with an express purpose beforehand, it's easy to read and use, though often software gets comprehensively documented, but never read.*

**F)** Why is it important to review the contents of your project notebook? *To figure out what worked/did not. It also ensures that you follow up on all the commitments that you've made or decisions that you've made, a really important aspect of professionalism and working with others.*

## 3.5. Summary of Section:

Note the following, from this section:

- Large software projects are more prone to errors/problems because of their size and complexity.
- Software is easy to change, but that malleability also makes it easy to break.
- Software development is similar to engineering principles: It defines clear activities, each of which has a end-product which is tested against the users requirements.
- For software development the basic process is as followed: Define how the dev process should operate, what activities are needed to be done, what is the life-cycle of the software, and how are the activities ordered - what is high priority?
    - Using tools or methods can enhance the abilities to answer these questions.
- Life-cycles can be sequential ([[../Glossary#^waterfall-def|Waterfall]]), iterative (Sculpting), incremental (Breadth) or a combination of all.
- Documentation levels should suit the task at hand and the environment.
- A disciplined approach requires that you take accountability to record and build documentation through recording your own actions at a personal and project level.
    - Personal = What have you done?
    - Project = What has been done to progress the overall solution?
- An [[../Glossary#^agile-def|Agile]] approach puts emphasis on people rather than processes/documentation, with shorter cycles of iteration, the acceptance that systems change, and cooperation.
***

# 4. Modelling in Software Development:

In this section we will cover the importance of models as part of software development, and discuss some popular processes.
## 4.1. Importance of Modelling:

Much of this module is concerned with the representation abstract concepts into models. This modelling approach


### 4.1.1. Agile Modelling:

### 4.1.2. A Standard Notation:

## 4.2. Models Illustrate Points of View:

## 4.3. Introducing the Unified Process (UP):

### 4.3.1. Views within the Unified Process:

### 4.3.2. Agile Unified Process:

## 4.4. Activities and Artefacts in the Development Process:

### 4.4.1. Domain Modelling:

### 4.4.2. Requirements:

### 4.4.3. Analysis:

### 4.4.4. Design:

### 4.4.5. Implementation:

### 4.4.6. Testing:

### 4.4.7. Deployment:

## 4.5. Summary of Section:

***

# 5. Unit Summary:




