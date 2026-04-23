---
date created: Thursday, March 26th 2026, 1:45:43 pm
date modified: Thursday, March 26th 2026, 2:12:39 pm
Gen: "1"
---

# Week 22-23 - Amazon Web Services (AWS):

# 1. Introduction:

In Part 2 we looked at the components involved in supporting a simple web site and how a cloud service such as OpenStack can provide these in a virtual setting. This part asks us to reflect on what we have seen of OpenStack and then both research and contrast that platform against **Amazon Web Services (AWS)**.

AWS is a mainstream platform providing a wide range of services, some very similar or equivalent to those seen in OpenStack. The main difference is that **OpenStack is open-source** while **AWS is proprietary**. An organisation may run its own OpenStack platform on its own machines (and alter the source code), whereas AWS must be outsourced and hosted on Amazon's infrastructure.

AWS began offering IT infrastructure services in **2006** and now provides a highly reliable, scalable, low-cost infrastructure platform powering hundreds of thousands of businesses in 190 countries.

---

# 2. Aims:

**After studying this part you should be able to:**

- Outline a range of services and operations of AWS required to run reliable and efficient web sites
- Outline the basis for costings under AWS
- Contrast AWS and OpenStack in terms of their differences at a high level and in service provision
- Draw some conclusions about the common components of mainstream cloud technologies such as OpenStack and AWS

---

# 3. An AWS Web Application:

A traditional web application has hardware components grouped into two parts: those connected to the internet outside the application's control, and those that are part of the web application itself (DNS server, NTP server, router/NAT, firewall, load balancer, web servers, and database).

The cloud utilises the same set of standards and protocols employed in traditional networks — DNS, NTP, routing, firewalls, and so on are all still required.

## 3.1. AWS Architecture:

The reference architecture for a scalable AWS website differs from traditional infrastructure in that the traditional NTP, DNS, router, NAT and firewall components are **missing** — they are provided by other means through AWS services.

The key AWS components in the architecture are:

- **Amazon Route-53** (DNS)
- **Amazon CloudFront** (edge caching / CDN)
- **ELB** (Elastic Load Balancing)
- **Amazon EC2** instances (web servers, automatically scaling)
- **Amazon S3** (object storage)
- **Amazon RDS** Master and Standby (database)

These are deployed within a **Region**, across multiple **Availability Zones**, inside a **Virtual Private Cloud (VPC)**.

### Region:

Amazon supports **27 regional centres** around the globe (including six in Europe) that provide the resources for AWS. Each region is completely independent and designed to be isolated from the other regions to maximise **fault tolerance and stability**.

### Availability Zones:

Each region contains multiple isolated locations known as **Availability Zones**. Each availability zone is designed as an independent failure zone — they are physically separated within a typical metropolitan region, located in lower risk flood plains, use discrete UPS and onsite backup generators, and are fed via different grids from independent utilities.

Distributing applications across multiple availability zones provides the ability to remain resilient in the face of most failure scenarios, including natural disasters or system failures.

### Virtual Private Cloud (VPC):

The starting point to building an AWS solution is the creation of a **Virtual Private Cloud (VPC)** — not to be confused with the private cloud deployment model described by NIST. A VPC exists within the AWS public cloud space, but it has a single owner (the tenant) and is **logically isolated** from other VPCs.

- A VPC is created within a region and initially contains a single availability zone
- The example architecture is split across **two availability zones** (A and B) so that should one fail, the application continues to run
- When created, the VPC is allocated a default network space of **10.0.0.0/16**, protected from other VPCs even though they share the same address range

### DNS (Amazon Route-53):

Amazon provides its own DNS service called **Amazon Route-53** to handle domain registration and directing internet traffic to the website. It is described as a highly available and scalable DNS web service.

### Static and Cached Content (S3 & CloudFront):

- **Amazon S3 (Simple Storage Service):** Durable and scalable object storage. Content can be served directly from S3 because each object (e.g. a file or image) has a unique HTTP URL
- **Amazon CloudFront:** Provides **edge caching** for websites — content is delivered from the edge of the AWS network rather than from deep within a single VPC. When new static content is requested from S3, it is moved out to the edge to reduce response time for future requests
- CloudFront is **not within the VPC** (it lies at the edge of the AWS network). S3 is located in the Region outside the VPC, but a **VPC endpoint** (gateway) can be configured inside the VPC to connect privately to the S3 service

### Elastic Load Balancing (ELB):

The **Elastic Load Balancing (ELB)** service is responsible for distributing requests within and across availability zones. It receives internet traffic and then distributes it to web servers.

**Key capabilities:**

- Monitors the **health** of web servers
- Can **dispose of underutilised servers** or **create new servers** as required
- Monitors its own usage so the service can expand to meet demand

### Servers (Amazon EC2):

All servers in the example are hosted on **Elastic Compute Cloud (EC2)** instances — the equivalent of a virtual machine (VM). An EC2 instance is created within an availability zone and connected to the ELB service.

- AWS uses its own image format, **Amazon Machine Image (AMI)**, and offers a wide choice of configured servers based on Linux and Windows operating systems
- Alternatively, the tenant can configure their own server and save it as an AMI
- The example deployment uses an **auto-scaling group** to automatically scale out as demand increases and scale down when demand falls

### Database (Amazon RDS):

The database is provided by **Amazon's Relational Database Service (RDS)**, which consists of a database instance running one of several popular database engines (e.g. MySQL, PostgreSQL, MariaDB, Oracle, MS SQL Server).

**High availability configuration:**

- Uses **multiple availability zones** — Amazon automatically provisions and maintains a **standby replica** of the database instance in a different availability zone
- Data from the master database is **synchronously replicated** to the secondary database

### Security:

AWS offers a range of security tools to define, enforce and manage access policies for the VPC:

- **IAM (Identity and Access Management):** Used to establish user accounts and set privileges to control access to different parts of a VPC
- **Console access:** Managed with private/public keys and SSH
- **EC2 instances** are locked down by default and cannot be accessed from outside the VPC
- **Software firewalls** combined with routing tables must be configured to enable data flow across subnets and to the internet
- **VPN option** available to connect a VPC to a corporate network
- **Data encryption:** Services cover data in transit (TLS) and at rest (public/private key encryption for RDS and S3 data)

### Management:

AWS offers two modes of control:

- A **web-based interface**
- A set of **APIs** for use with RESTful web services and program codes

Using these tools, a tenant can launch new instances, review existing ones, build auto-scaling plans, manage security, manage storage and monitor usage.

---

# 4. AWS Reading and Research:

## 4.1. Activity 1 — AWS General Research (4–6 hours):

It is important to examine AWS and look for aspects which are common between AWS and OpenStack, and where they differ. Common aspects are probably mainstream and will become standards in time.

**Areas to research and be able to discuss:**

- AWS components required to support a simple web site (HTML/JavaScript pages, server-side business logic, database)
- Networking aspects: Internet access, DNS, public and private networking, addressing (CIDR)
- Security of applications and data: access rules, credentials, tenant/network privacy, user access levels, read-only vs data entry applications
- Data security: backup and replication
- Load balancing: improving response speed and reliability
- Autoscaling / elasticity: increasing and reducing resources (VMs, networking, data access) in reaction to demand, including health monitoring and server restarts
- Costs: what are they based on (type and usage of resources such as VM, memory, storage, database size, traffic)

**Key AWS documentation links:**

- AWS Documentation: <https://aws.amazon.com/documentation/>
- AWS Whitepapers: <https://aws.amazon.com/whitepapers/>
- AWS Global Infrastructure: <https://aws.amazon.com/about-aws/global-infrastructure/>
- Regions and Availability Zones: <http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html>
- Amazon VPC: <https://aws.amazon.com/vpc/>
- Amazon Machine Images (AMI): <http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html>
- Amazon Route 53: <https://aws.amazon.com/route53/>
- Autoscaling: <http://docs.aws.amazon.com/autoscaling/latest/userguide/WhatIsAutoScaling.html>
- Amazon EC2: <https://aws.amazon.com/documentation/ec2/>
- Elastic Load Balancing: <https://aws.amazon.com/elasticloadbalancing/>
- Amazon S3: <https://aws.amazon.com/documentation/s3/>
- Amazon RDS and DynamoDB: <https://aws.amazon.com/free/databases-free-tier/>

## 4.2. Activity 2 — Costing Estimate Research (15–30 minutes):

Determine what it might cost to set up a website on AWS based on:

- All servers use the **Linux** operating system
- Web servers run **Apache** software
- Database server runs **MySQL**
- Minimum rental of **three months** of 24/7 availability

## 4.3. Activity 3 — Practice Quiz (1 hour):

Complete the Practice quiz: OpenStack and AWS.

---

# 5. Comparing AWS and OpenStack:

|Aspect|OpenStack|AWS|
|---|---|---|
|**Type**|Open-source project|Proprietary cloud solution|
|**Hosting**|Can be run in-house on own machines|Must be hosted on AWS infrastructure|
|**Source code**|Can be altered as required|Not accessible or modifiable|
|**Compute**|Nova (VMs)|EC2 (instances using AMIs)|
|**Object Storage**|Swift|S3 (Simple Storage Service)|
|**Networking**|Neutron (virtual networks, routers)|VPC (Virtual Private Cloud)|
|**DNS**|Designate|Route-53|
|**Load Balancing**|LBaaS (Octavia)|Elastic Load Balancing (ELB)|
|**Database**|Trove|RDS (Relational Database Service)|
|**Orchestration**|Heat (HOT templates in YAML)|CloudFormation|
|**Autoscaling**|Heat AutoScalingGroup with Aodh alarms|Auto Scaling Groups with CloudWatch|
|**Security**|Security groups, key pairs, tenant isolation|IAM, security groups, SSH keys, VPC isolation|
|**CDN / Caching**|Not built-in (third-party)|CloudFront (edge caching)|
|**Management**|Horizon dashboard + APIs|Web console + APIs (RESTful)|
|**Infrastructure**|Regions concept varies by deployment|27+ regions with multiple Availability Zones|

---

# 6. Summary:

In this part we have seen some basic elements of AWS and been given a range of leads for further research. It is important to have seen sufficient of AWS to both sketch out an application architecture and comment on the commonality and differences with OpenStack.

**Key concepts covered:**

- **AWS** is a proprietary cloud platform hosted by Amazon, contrasting with OpenStack's open-source, self-hosted model
- **Regions and Availability Zones** provide fault tolerance and stability — regions are independent, and availability zones within regions are physically separated failure zones
- **VPC (Virtual Private Cloud)** is the starting point for an AWS solution, providing logically isolated networking within the public cloud
- **Route-53** provides DNS services, replacing the need for local DNS servers
- **S3** provides scalable object storage, and **CloudFront** provides edge caching to reduce response times
- **ELB (Elastic Load Balancing)** distributes requests across availability zones and monitors server health
- **EC2** instances are virtual machines using Amazon Machine Images (AMIs), with auto-scaling groups for elasticity
- **RDS** provides managed relational databases with high availability through multi-AZ replication
- **Security** is managed through IAM, SSH keys, software firewalls, routing tables, VPNs, and encryption (TLS in transit, public/private keys at rest)
- **Management** is available through both a web interface and RESTful APIs
- Both AWS and OpenStack share common cloud concepts (compute, storage, networking, load balancing, autoscaling) but differ in naming, implementation details, and deployment model

---