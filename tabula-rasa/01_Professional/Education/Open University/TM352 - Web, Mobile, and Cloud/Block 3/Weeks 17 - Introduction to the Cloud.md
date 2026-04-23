---
date created: Thursday, March 26th 2026, 1:44:58 pm
date modified: Thursday, March 26th 2026, 1:52:14 pm
Gen: "1"
---

# Week 17 - Introduction to the Cloud:

# 1. Introduction:

Welcome to Block 3 of TM352, which examines cloud technology. Block 3 comprises five parts and a TMA, allocated 10 weeks. The first two parts are not difficult, but do not let them lull you into a false sense of security — a lot of effort is required to complete the block in its entirety. The practical activities may be demanding and might need to be attempted and repeated more than once.

In Parts 2 and 3 you will be using a cloud infrastructure platform called 'OpenStack', made available on an OU server. You are asked to limit the resources you use on the server and not leave virtual machines, floating IP addresses, etc. in use when not absolutely necessary.

It seems no matter where you turn you will find some mention of the 'cloud' and how this new model of computing is set to change the way consumers, businesses and governments interact. If you subscribe to Netflix or use Dropbox then you are already a consumer of cloud services — both use Amazon Web Services (AWS) to host their applications and store their data.

In simple terms, computing power can be bought as virtual CPUs per hour, storage as gigabytes per month, and networking as gigabytes transmitted and received. You pay for what you use, just as you do for utilities.

---

# 2. Aims:

**After studying this part you should be able to:**

- Briefly describe the three service models of the cloud
- Explain the four deployment options for a cloud
- Prepare a list of the key differences between virtual machines and containers
- Draft your own definition for the cloud

---

# 3. Defining the Cloud:

If you use Facebook, X, Dropbox, YouTube, Gmail, or other social media via a PC, tablet or phone, you are already using the cloud. The companies behind these tools use vast data centres housing servers, databases and networking equipment to support millions of users worldwide.

From a consumer's point of view, we don't really care about the servers, storage and networking — we just want assurance that an application is accessible via our chosen device from our current location.

The big social media applications share common features:

1. Use the internet for communication
2. Have grown to handle millions of users
3. Support multiple user devices
4. Are accessible from any location

## 3.1. NIST Definition of Cloud Computing:

The well-respected definition from Mell and Grance of the National Institute of Standards and Technology (NIST) defines cloud computing as:

> Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction. This cloud model is composed of five essential characteristics, three service models, and four deployment models. — (Mell and Grance, 2011, p. 2)

---

# 4. Characteristics of the Cloud:

The NIST document defines five essential characteristics:

## 4.1. On-Demand Self-Service:

A consumer can unilaterally provision computing capabilities (server time, network storage) as needed automatically without requiring human interaction with each service provider.

The "consumer" here refers to the owner of the hosted application (e.g. a company providing Office 365 to employees), not the end-user. The term "provision" is synonymous with creating the infrastructure to host an application. An implication of "on demand" is that IP addresses and DNS entries must be assigned dynamically, whereas traditional web hosting relies on static IP addressing.

## 4.2. Broad Network Access:

Capabilities are available over the network and accessed through standard mechanisms that promote use by heterogeneous thin or thick client platforms (mobile phones, tablets, laptops, workstations).

Standard mechanisms include network protocols (TCP/IP), communication protocols (HTTP), presentational standards (CSS), structural standards (HTML), plus standards for routing, DNS, video and audio file formats.

## 4.3. Resource Pooling:

The provider's computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to demand. The customer generally has no control or knowledge over the exact location of resources but may specify location at a higher level of abstraction (e.g. country, state, or datacenter).

A key difference from conventional shared hosting is that within the cloud, everything is done dynamically — the customer can add more processors, memory and disk storage to their server.

## 4.4. Rapid Elasticity:

Capabilities can be elastically provisioned and released, in some cases automatically (orchestration), to scale rapidly outward and inward commensurate with demand. This is one of the most distinctive characteristics of the cloud — the ability to increase resources as demand rises and dispose of resources as demand falls.

The traditional web hosting model makes scaling expensive because physical resources must be in place regardless of need. The cloud permits scaling on demand — a duplicate web server can be up and running within a few minutes.

## 4.5. Measured Service:

Cloud systems automatically control and optimise resource use by leveraging a metering capability appropriate to the type of service (storage, processing, bandwidth, active user accounts). Resource usage can be monitored, controlled, and reported, providing transparency for both provider and consumer.

The management tools are more powerful than traditional hosting, allowing full control of your cloud through an application programming interface (API).

---

# 5. Service Models of the Cloud:

The three service models defined by NIST are key to understanding how the cloud has evolved.

**Note:** The NIST document uses the term "consumer" to define the individual or organisation using the cloud. The current trend is to use the term **"tenant"**, drawing on the analogy of someone who rents accommodation.

## 5.1. Software as a Service (SaaS):

The capability provided to the consumer is to use the provider's applications running on a cloud infrastructure. Applications are accessible from various client devices through a thin client interface (e.g. web browser) or a program interface. The consumer does not manage or control the underlying cloud infrastructure.

**How it works:** The entire application and hosting infrastructure is the responsibility of the service provider. Tenants share the application, middleware, operating system and hardware, but have their own protected application data.

**Examples:** Netflix, Dropbox, Adobe (converted from stand-alone to web-based SaaS delivery). Organisations can also use SaaS for email, word processing and other office tools.

## 5.2. Platform as a Service (PaaS):

The capability provided is to deploy onto the cloud infrastructure consumer-created or acquired applications created using programming languages, libraries, services, and tools supported by the provider. The consumer does not manage the underlying infrastructure but has control over deployed applications and possibly configuration settings.

**How it works:** The tenant creates the application hosted by the PaaS provider. For example, a tenant might contract for a web server with scripting engine plus a database server, but have limited choice over the OS or database engine. The tenant's options cover the application and its data, but middleware, OS and hardware remain under the service provider's control.

Most PaaS providers add value via pluggable services such as authentication, email, UI components, and an API to monitor and manage the application.

**Examples:** AWS, Google App Engine, Microsoft Azure, Oracle Cloud.

## 5.3. Infrastructure as a Service (IaaS):

The capability provided is to provision processing, storage, networks, and other fundamental computing resources where the consumer can deploy and run arbitrary software, including operating systems and applications. The consumer does not manage the underlying cloud infrastructure but has control over operating systems, storage, deployed applications, and possibly limited control of select networking components (e.g. host firewalls).

**How it works:** The tenant takes responsibility for most of the application but not the computer or networking infrastructure. Comparable to renting a dedicated host to run a web server or database server. The tenant's options include the middleware, but hardware and OS remain under the service provider's control. Most IaaS providers offer tenants a choice of OS from a restricted set of "flavors".

**Examples:** AWS Elastic Compute Cloud (EC2), Rackspace, Microsoft Azure, Google Compute Engine.

---

## 5.4. Layered Architecture:

Mell and Grance refer to a cloud infrastructure as containing both a **physical layer** and an **abstraction layer**:

- **Physical Layer:** The actual hardware required to host the cloud service (Server, Storage & Network)
- **Abstraction Layer:** The software deployed to implement the service, containing the three service models in a hierarchy:
    - Applications (SaaS) — top
    - Software (PaaS) — middle
    - Infrastructure (IaaS) — bottom

The hierarchy represents the fact that cloud services can be composed of one or more other cloud services. A company offering SaaS could do so by contracting for a PaaS, and the PaaS provider could build on an IaaS offering. It is also possible to build SaaS directly on the physical layer, provided PaaS and IaaS functionality is implemented as part of the application.

---

# 6. Deployment Models of the Cloud:

The NIST cloud definition describes four deployment models:

## 6.1. Private Cloud:

The cloud infrastructure is provisioned for exclusive use by a single organisation comprising multiple consumers (e.g. business units). It may be owned, managed and operated by the organisation, a third party, or a combination, and may exist on or off premises.

Historically regarded as the only solution for organisations needing to protect sensitive data or comply with privacy legislation. The typical solution was a private data centre, but modern solutions allow hosting private clouds in public data centres.

## 6.2. Public Cloud:

The cloud infrastructure is provisioned for open use by the general public. It may be owned, managed and operated by a business, academic, or government organisation. It exists on the premises of the cloud provider.

This is the cloud everyone knows and uses. Providers like Amazon, Microsoft and Google have constructed vast data centres. To simplify compliance with privacy laws, large providers have built data centres in separate legal jurisdictions.

## 6.3. Hybrid Cloud:

The cloud infrastructure is a composition of two or more distinct cloud infrastructures (private, community, or public) that remain unique entities but are bound together by standardised or proprietary technology enabling data and application portability (e.g. cloud bursting for load balancing between clouds).

The private–public hybrid has become popular for large enterprises that use a private cloud for compliance and gain public cloud benefits for customer-facing applications. Modern technologies allow co-locating private and public elements within a single data centre.

## 6.4. Community Cloud:

The cloud infrastructure is provisioned for exclusive use by a specific community of consumers from organisations with shared concerns (mission, security requirements, policy, compliance). May be owned and operated by one or more community organisations, a third party, or a combination.

Community clouds combine features of private (restricted access) and public (shared data and applications). A common scenario is a community of employees, partners and customers created so customers and partners can provide better feedback.

---

# 7. Other Cloud Models:

The NIST document describes three basic service models, but as the cloud evolved, many essential components have been decomposed into self-contained services based on service-oriented architecture (SOA) — complex processes split into small re-usable web service components.

## 7.1. UCSB and IBM Cloud Model:

The University of California Santa Barbara (UCSB) and IBM layered cloud model comprises **five layers** (two more than NIST), developed to aid in exploration and teaching of cloud computing (Ahson and Ilyas, 2010, p. 5).

**Layers (bottom to top):**

1. **Firmware/Hardware (HaaS):** Hardware as a Service — the cloud provider maintains and updates hardware as a service
2. **Software kernels and middleware:** Systems software that creates, manages and schedules the abstraction layer software. Tenants of higher-level services have no visibility of this layer
3. **Cloud software infrastructures** — split into three distinct services:
    - **IaaS** — Computational resources
    - **DaaS** — Data storage as a Service
    - **CaaS** — Communication as a Service
4. **Cloud software environments (PaaS)**
5. **Cloud applications (SaaS)**

Splitting infrastructure into separate services (IaaS, DaaS, CaaS) increases flexibility for the tenant and creates opportunity for the provider to add value. Applications that need database features can plug in DaaS; those needing special networking (high bandwidth, encryption, isolation) can add CaaS.

## 7.2. Hoff's Cloud Model:

Developed by Christofer Hoff for professional presentations about cloud security (Hoff, 2009). This is a much more detailed model bringing to the fore many elements hidden within the NIST and UCSB+IBM models.

**IaaS block (five layers):**

1. **Facilities:** Data centre facilities — power, cooling (HVAC), equipment rack space
2. **Hardware:** Actual computers, network and data storage equipment (Compute, Network, Storage)
3. **Abstraction:** Hypervisor or cluster management software
4. **Core Connectivity and Delivery:** Essential network services — DNS, load balancing, security, authentication
5. **APIs:** Application programming interface for tenant management, monitoring and control

**PaaS block:**

- **Integration and Middleware:** Database, messaging, queuing, authentication services that support cloud functioning (not tenant services)

**SaaS block (four layers):**

1. **Data, Metadata, Content:** Application data (structured and unstructured)
2. **Applications:** Native, web, or emulated applications
3. **APIs:** Application management interface
4. **Presentation Modality & Presentation Platform:** Processing different data types (binary, video, voice) for delivery to different devices (PC, mobile, embedded)

**Commercial examples mapped:** Amazon EC2 (IaaS), Google App Engine (PaaS), Salesforce/Google Apps/Oracle On Demand (SaaS).

## 7.3. Choosing a Model:

The NIST, UCSB+IBM and Hoff models provide increasingly detailed visions of cloud composition. The level of detail required depends on the end goals:

- Migrating employees to cloud-based email → NIST model is sufficient
- Implementing regulatory requirements for email usage (e.g. financial sector) → Hoff's detailed model becomes a powerful tool

---

# 8. How the Cloud Arose:

Two crucial concepts underpin the cloud: **virtualisation** and **scaling**.

## 8.1. Virtualisation:

Virtualisation is the core technology of the cloud, emerging from improvements in processor chip design.

**Moore's Law:** In 1965, Gordon E. Moore observed that the number of components in a dense integrated circuit doubled approximately every year. He revised this to every two years in 1975. Almost 40 years later this projection remains on target — the Motorola 68000 CPU (~1980) contained ~100,000 transistors; by 2011 the Intel Xeon 10-core CPU reached 2,600,000,000 transistors.

The growth of raw processing power means the typical single-application server is under-utilised, running at less than 10–15% of its potential (Golden, 2009). The solution is virtualisation, where a special layer of software separates and secures multiple applications within a single physical host.

**Two forms of virtualisation:**

- Virtual machines
- Containers

### Virtual Machines:

VM virtualisation takes the resources of a single physical host computer (CPUs, memory, I/O devices) and shares them between multiple guest computers. Each guest appears to be an independent, self-contained computer with its own processor, memory and peripherals, running a standard operating system.

**How it works:**

- A basic stand-alone computer loads the OS into memory along with device drivers, then applications
- Applications make requests to the OS for I/O tasks; the OS makes requests to low-level drivers for actual data transfer
- In a virtualised system, the **hypervisor** manages and protects virtual servers, handling device drivers, creating VMs, protecting memory space, scheduling processors, and cleaning up when VMs are disposed of
- Each VM contains a **guest OS** with **virtual drivers** — virtual because they don't directly control I/O devices. When a guest OS needs I/O, it requests through the virtual driver → hypervisor → real driver

**Benefits of VMs:**

- Overcome poor utilisation by enabling a single host to support multiple guests
- Guest configurations (processors, memory, disk) can be defined to meet specific requirements (e.g. simple web server: 1 vCPU + 512 MB; PHP web server: 2 vCPUs + 2 GB)
- Configurations can be saved as VM images and loaded multiple times

### Containers:

VMs come with significant overhead — the entire OS must be loaded before any application can start, consuming lots of memory and requiring full boot-up time.

The solution is the **application container** — a file containing an application and associated libraries with no separate operating system, making it much smaller (megabytes instead of gigabytes).

**How containers work:**

- The **Container Management** layer manages loading/unloading containers, using the OS's features to isolate and secure individual applications
- Isolation between host and container is not as strong as hypervisor-based virtualisation because all containers share access to the host
- Containers have **direct access to device drivers** through the OS, rather than virtual device solutions, speeding up I/O operations

**Benefits of containers:**

- Minimal administrative workload — security configuration, user accounts, file system protection done just once
- **Docker** is one of the most popular containerisation tools, with support from Amazon, Google and Microsoft
- Docker aims to enable container migration to any OS supporting Docker software, helping tenants avoid lock-in

**VMs vs Containers comparison:**

|Feature|VMs|Containers|
|---|---|---|
|Size|Large (GBs — includes full OS)|Small (MBs — app + libraries only)|
|Start-up time|Minutes (full boot-up)|Seconds (no boot-up)|
|Admin costs|High (each VM needs OS config, accounts, security)|Low (done once on host)|
|Licencing costs|Potentially higher (OS licence per VM)|Lower (shared host OS)|
|Security|Strong isolation via hypervisor|Weaker isolation (shared host access)|
|Density|Dozen or two dozen per server|Hundreds per server|

---

## 8.2. Scaling:

All servers have processing limits. As more users request pages, workload increases until the processor runs flat out, further requests queue, and eventually the server responds with a "busy" message. Overwhelming a server is the basis of a distributed denial of service (DDoS) attack.

### Scaling-Out:

Multiple web servers operate in parallel to share workload. A **load balancer** receives all incoming requests and redirects them to one of the attached web servers.

**Load balancing algorithms:**

- **Round robin:** Requests assigned sequentially (request 1 → server 1, request 2 → server 2, etc.)
- **Modern load balancers:** Monitor connected servers and exclude failed ones, increasing workload on remaining servers but ensuring a response

**Availability:** Scaling out increases website availability — the probability the site is available for use. Availability is calculated as:

```
A = Uptime / (Uptime + Downtime)
```

|Target|Availability|Downtime per year|
|---|---|---|
|Retail web application|99.9%|8 hours 45 minutes|
|Financial transactions|99.999%|5 minutes 15 seconds|

**Stateless requirement:** For scaling-out, any request must be fulfillable by any server. Applications must be "stateless" — not relying on the server to remember state from previous requests. Cookies are commonly used to carry state, or state can be saved in a shared database with a cookie carrying a user identifier.

### Scaling-Up:

Additional resources are added to a computer to increase its performance. Rarely encountered physically (few computers have empty processor sockets), but virtualisation makes it possible — a VM can be redefined from 1 processor + 1 GB memory to 2 processors + 2 GB memory.

---

## 8.3. Virtualisation and Scaling:

The combination of virtualisation and scaling is fundamental to the cloud — this is how **elasticity** is achieved. As demand grows, a new VM is launched; it is removed when demand falls.

**How it works:**

- An **image store** holds VM image files (e.g. load balancer, Apache web server, MySQL database server)
- A **configuration template** configures each VM as it is launched (IP addresses, network, disk storage, access controls)
- The application might start with a single web server; as demand increases, more servers are launched from the same image but individually configured

### Flavors:

To maximise use of a single host, most cloud providers offer a limited number of guest configurations known as **"flavors"** — defining the number of processors, memory and local disk storage allocated to a guest.

**OpenStack flavors example (packing model):**

|Flavor|vCPU|Virtual Memory|Total vCPU (count × per)|Total vMemory|
|---|---|---|---|---|
|8 × Small|1|0.5 GB|8|4 GB|
|4 × Medium|2|1 GB|8|4 GB|
|2 × Large|4|8 GB|8|16 GB|
|1 × XLarge|8|16 GB|8|16 GB|
|**Total**|||**32**|**40 GB**|

**Overcommit ratio:** The ratio of available virtual resources to available physical resources. OpenStack defaults are 16:1 for CPUs and 1.5:1 for memory. A host with 10 cores could support guests up to 160 vCPUs, provided total virtual memory is less than 1.5× actual memory.

The above combination of flavors falls within the design limits of a quad-core processor with 32 GB of memory.

---

# 9. Summary:

The first half of this part introduced important descriptions and models of the cloud. The NIST description (2011) continues to receive wide industry support. The characteristics, service models and deployment models provide a good introduction, but lack details essential for decision making. The UCSB+IBM and Hoff layered architecture models more clearly show the true nature of the cloud.

The second half examined two key underpinning technologies:

**Virtualisation:**

- **VMs** comprise an OS, device drivers and application software running under a host OS with a hypervisor for isolation
- **Containers** comprise an application and libraries within a single package running directly under the host OS — smaller, quicker to load, start in seconds rather than minutes

**Scaling:**

- **Scaling-out** distributes work across multiple servers via load balancing
- Cloud providers manage VMs on a host using template configurations (flavors)
- Launching a VM is just part of the story — VMs also need load balancing, networking, routing, security (authentication and authorisation), all created and assigned dynamically

---

# 10. References:

- Ahson, S. and Ilyas M. (eds) (2010) _Cloud Computing and Software Services: Theory and Techniques_, Taylor and Francis, p. 5.
- Cacciatore, K. et al. (2015) _Exploring Opportunities: Containers and OpenStack_, p. 8. Available at: <https://www.openstack.org/assets/pdf-downloads/Containers-and-OpenStack.pdf>
- De Jesús, J. (2012) _Navigating the IBM cloud, Part 1: A primer on cloud technologies_, p. 8. Available at: <https://jdejesus001.medium.com/navigating-the-ibm-cloud-d1a380f8fba8>
- Golden, B. (2009) _Virtualization for Dummies_, Indianapolis (Indiana), Wiley Publishing, Inc.
- Hoff, C. (2009) 'Cloud Computing Taxonomy & Ontology', _Rational Survivability_. Available at: <http://www.rationalsurvivability.com/blog/2009/01/cloud-computing-taxonomy-ontology-please-review/>
- Mell, P. and Grance, T. (2011) _The NIST Definition of Cloud Computing_. Available at: <http://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf>
- Moore, G. (1965) 'Cramming more components onto integrated circuits', _Electronics_, pp. 114–17.
- Moore, G. (1975) 'Progress in Digital Integrated Electronics.' _Technical Digest–IEEE International Electron Devices Meeting_, pp. 11–13.
- OpenStack (2016) _OpenStack Architecture Design Guide_. Available at: <https://docs.openstack.org/arch-design/>

---