---
date created: Thursday, March 26th 2026, 1:45:43 pm
date modified: Thursday, March 26th 2026, 2:15:39 pm
Gen: "1"
---

# Week 24 - Benefits and Risks of the Cloud:

# 1. Introduction:

In the previous parts of this block we explored what is meant by the cloud — the basic service models (SaaS, PaaS, IaaS), the deployment models (public, private, hybrid, community), and architectural models (NIST, USBC+IBM, Hoff). We saw how a scalable web application's functionality could be reproduced within OpenStack by exchanging traditional hardware components for equivalent software services, and investigated the alternative AWS cloud solution.

This part addresses the question: **what is driving the migration to the cloud?** Cost is the biggest driver, but significant benefits also come from greater **elasticity** and **resilience**, and a shift from **capital to operational expenditure**.

**Security and privacy** are cited as the biggest risks associated with the cloud. There are legal requirements imposed on organisations that collect, store and exchange data linked to individuals. Key legislation includes the **EU Directive 95/46/EC** (1995), the **UK Data Protection Act** (1998, replaced 2018), and the **General Data Protection Regulation (GDPR)** which came into force in May 2018.

---

# 2. Aims:

**After studying this part you should be able to:**

- Explain how elasticity and pay per use can help reduce the total cost of ownership (TCO) for an organisation
- Discuss why the distributed data model of the cloud might raise concerns relating to data privacy and data protection
- Briefly outline current European legislation for data protection as it pertains to cloud computing
- Describe the security options you might use to protect data in transit and data at rest

---

# 3. Benefits of the Cloud:

There are numerous benefits claimed for the cloud. This part focuses on four: **elasticity**, **resilience**, **operational vs capital expenditure**, and **cost**.

## 3.1. Elasticity:

One of the core benefits of the cloud is **elasticity** — the ability to automatically expand resources as demand increases and shrink resources as demand wanes. Running instances are continuously monitored to ensure they respond to requests and perform within operational limits. Should an image fail or exceed its performance limits, a new instance is launched to replace or supplement it.

AWS and OpenStack also offer the option to **schedule** the launch of additional instances to meet expected demand (e.g. an online store scheduling extra resources as different geographic regions enter working hours).

**Traditional deployment vs cloud deployment:**

- **Traditional (fixed capacity):** Hardware is deployed in instalments. Capacity always exceeds predicted demand, but at the cost of surplus capacity throughout the application's life. Real demand exhibits peaks and troughs — at times demand may briefly exceed fixed capacity (lost requests), and if demand grows faster than predicted, even additional capacity installed later cannot satisfy it. Traditional hosting infrastructure takes time to select, order, install and configure, so there are always periods of over-provisioning or under-provisioning.
- **Cloud (elastic capacity):** As demand increases, new resources are brought online. When demand falls, resources are removed. The capacity curve always exceeds demand — no lost requests and very little underutilisation of equipment.

**Critical elasticity targets** for a cloud service provider (Leong, 2014):

- Provision a new Linux VM in under five minutes
- Resize a VM without stopping execution
- Provide autoscaling based on a schedule or monitoring trigger
- Provide sufficient capacity to enable a customer to exceed their normal baseline by a factor of ten in real time and without prior notice

## 3.2. Resilience:

**Resilience** is a measure of the availability of a VM instance. The concern is the reliability of the **physical host** of the VMs, and the key factor is the ability to quickly detect a problem with the host and migrate VMs to another host with minimal loss of service.

AWS achieves resilience by offering clients the option to configure VMs into **multiple availability zones**. If one zone fails, another can take over the workload and launch additional VMs without loss of service (though some degradation may occur as new VMs are launched). Moving VMs between availability zones can also mitigate loss of service during regular maintenance downtime.

**Critical resilience capabilities** (Gartner / Leong, 2014):

- Detection of physical host failure and automatic restart of VMs on another host
- Reduced maintenance downtime by live migration of VM
- Automated replication across data centres

## 3.3. Operational Vs Capital Expenditure:

**Operational expenditure (OpEx):** Covers rent, salaries and expenses of running a business. Often devolved to departments with few central controls.

**Capital expenditure (CapEx):** Covers costs of purchasing business assets (machinery, vehicles, computing equipment). Assets form part of the business's value, are recorded in annual accounts, depreciate over time, and some loss in value can be offset against UK tax liabilities. Capital expenditure is generally centrally controlled.

**Why this matters for the cloud:** If an IT project requires significant equipment investment, someone must make a case for capital expenditure and get approval — this could take months before the actual work begins. The cloud alternative could be set up in a few days and paid for from the department's operational budget. For small organisations, running costs could be covered by cash flow generated by the application.

This is especially important for **start-ups** that can conserve capital by renting resources, and for any company pursuing IT projects that has difficulty obtaining capital upfront.

## 3.4. Costs:

A major benefit claimed by cloud providers is cost, with quoted savings for migrating to AWS averaging more than **$500,000 per year** (IDC report, sponsored by Amazon).

### Infrastructure Costs:

The biggest contributor to savings (approximately **$275,000/year**) came from reduction in infrastructure and services costs. Data centres are expensive to build and operate. Key cost factors include: air conditioning, multiple electricity providers, backup generators, multiple ISPs, and duplicated equipment (routers, switches, load balancers) to remove single points of failure.

Moving from physical to virtual servers increases server utilisation and decreases administration costs. IDC found that 11 organisations replaced an average of **400 physical servers** and saved over **$190,000**. A further **$50,000** was saved in co-location and management fees, **$21,000** on network equipment and bandwidth, and **$13,000** by switching to cloud storage.

### Staff Costs:

Staff costs can rise to **80%** of the maintenance phase costs. IDC found migrating to the cloud could produce staff-cost savings of more than **$145,000/year** and reduce overall developer hours by **80%**.

Key improvements from using AWS: development and testing tasks performed **5x faster**, integration phase output **doubled**, deployment phase output increased by **4.5x**. The key contributing factor was the AWS API, which reduced time spent writing custom code. Automated provisioning, dynamic scalability, management and monitoring mean many services no longer need to be coded — they can simply be configured as part of deployment.

### Sample TCO Comparison (AWS Three-Year):

|Cost Category|Co-location|AWS|
|---|---|---|
|**Server**|$171,599|$73,399|
|**Storage**|$58,263|$1,535|
|**Network**|$53,067|$3,755|
|**IT-Labour**|$210,000|$140,000|
|**Total**|$492,889|$218,689|

### AWS Pricing Options for EC2:

- **On-demand (pay-per-use):** Pay for what you use
- **Reserved instances:** Cheaper over time but you pay the hourly rate even when instances are not used. Saves approximately $50,000 over three years compared to on-demand
- **Spot instances:** Spare capacity offered to users who bid a maximum price per instance-hour. You get instances until you terminate them or the spot price exceeds your bid

### Intangible Costs to Consider:

- **Reliability and availability:** Measured by downtime; governed by Service Level Agreements (SLAs)
- **Data centre quality:** Classified by Uptime Institute into Tier I (basic — UPS and backup generator) through Tier IV (fault-tolerant environment)
- **Interoperability:** How easy is it to integrate with other applications or adapt to the cloud provider's API
- **Security and privacy:** May require specific policies to satisfy regional legislation
- **Training:** Skills and knowledge of existing staff; may need training and certification

---

# 4. Risks of the Cloud:

Moving an application from a closed private environment onto the public cloud presents complex issues. Instead of dedicated IT equipment under close supervision, applications and data are hosted on **shared resources** with little direct control of where those resources are located. The **multi-tenancy** model means your VM will be co-hosted with VMs of other users — the only barrier between VMs is the **hypervisor**, unless other steps are taken.

Securing data makes good business sense but may also be a **legal requirement**. The EU has enacted regulations and directives covering individuals' rights to privacy and protection of personal data, including rules governing **trans-border data flows**.

## 4.1. Data on the Move:

### Security Domains:

The starting point for any security assessment is to identify what needs to be secured and from whom. A common approach is to establish **security domains** with assigned trust levels:

- **World domain:** Untrusted users accessing an application from the internet
- **Public domain:** Contains the web server accessed via the internet. Higher trust than a user, but since it could be compromised, access to the private domain should be restricted
- **Private domain:** Contains application and database servers. Assigned the highest level of trust to ensure they can intercommunicate

In the cloud, a single compute host houses multiple tenant VMs, which introduces a **horizontal dimension** to the domains to ensure the integrity of each VM. Data flows are more complex because VMs access the network via the physical interfaces of the host, and some data paths must bridge security domains.

### OpenStack Security (Data in Transit):

**Approach 1 — Separate networks:** Use separate networks for management data and VM traffic. All access to storage devices is restricted to the management network, secured by TLS.

**Approach 2 — Layer 2 isolation:** Uses software defined networking (SDN) to implement Layer 2 and Layer 3 protocols. A popular option is **VLANs**, where each tenant is allocated a VLAN identifier that functions as a unique tag in an ethernet packet header. All interfaces sharing the identifier become part of an isolated broadcast domain.

**Bridging security domains:** Data crossing domains (e.g. internet user accessing the OpenStack RESTful API) requires **HTTPS with TLS certificates**. However, HTTPS is a point-to-point protocol:

- **(a)** Internet → Web Server: HTTPS works fine for a direct connection
- **(b)** Internet → Load Balancer → Web Server: First hop is secure, second is not
- **(c)** Solution: A **proxy service** on the load balancer acts as the HTTPS client and passes the secure connection request to the web server

Externally facing equipment should use TLS certificates chaining to a **trusted root CA** distributed with popular browsers. Internal link certificates do not need to chain to a trusted root.

**Data disposal:** When a VM shuts down, memory and ephemeral disk space are released back to the shared pool. The next VM could access private data through that memory or disk. Best practice is to **sanitize cloud system media** prior to disposal, release, or reuse.

### AWS Security (Data in Transit):

AWS defines a **shared security responsibility model:**

- **AWS is responsible for:** Protecting the global infrastructure (hardware, software, networking, facilities)
- **The tenant is responsible for:** Security configuration and management of IaaS products (EC2, VPC, S3), including guest OS management, updates, security patches, application software, and firewall (security group) configuration

**Key AWS security features:**

- All AWS services (S3, ELB, Route 53) offer **secure access points** using HTTPS/TLS
- API access is protected by **user credentials** passed in REST requests
- VPC access is managed by **firewall** (default "deny all") and **access control lists (ACLs)**
- VPC traffic may be restricted by protocol, service port, or source IP address (individual IP or CIDR)
- **S3 server-side encryption:** AWS generates a unique symmetric key per object, encrypts using **AES-256**, then encrypts the key with a master key stored securely and rotated regularly
- Tenants can alternatively manage their own keys and encryption/decryption process
- **VM isolation** relies on the **Xen hypervisor** and the AWS firewall between the host's physical network interface and VM's network interface
- The hypervisor ensures **isolation of physical RAM** and scrubs memory when released by a VM (memory not returned to the free pool until scrubbing is complete)
- **Ephemeral disks** are cleaned by a proprietary disk virtualisation layer

## 4.2. Data at Rest:

Securing data at rest concerns the encryption of data on disks — either as objects in an object store or as data tables within a database.

### Key Management Infrastructure (KMI):

Most data encryption uses **symmetric keys** (a single key for both encryption and decryption), so securing the key is critical. Options relying on trusted users to provide passwords are not practical at cloud scale. A **Key Management Infrastructure (KMI)** combines securely storing keys with authorising key usage.

**OpenStack KMI:** The **Barbican** key management service exists but was at early development stages. File security is based on OS features (access control lists, API tokens). Database security relies on server hardening and the authentication/authorisation features of the database engine (e.g. MySQL).

**AWS KMI — three options:**

- **Option 1:** Tenant takes full responsibility for the KMI
- **Option 2:** Tenant manages keys and data processing; AWS takes responsibility for key security
- **Option 3:** AWS takes full responsibility for the KMI (can be as simple as setting a checkbox in the AWS dashboard)

Options 1 and 2 require the tenant to write code for key management and encryption/decryption. Option 3 requires minimum tenant input.

---

# 5. Privacy:

Privacy is one of the key issues surrounding growth of the cloud. Companies are concerned about **where their data is stored** and users are concerned about **who might have access** to their personal information.

The right to privacy appeared in **Article 12** of the United Nations Universal Declaration of Human Rights (1948). The **European Convention on Human Rights** (1950) guarantees the right to respect for private and family life, home and correspondence.

Most data collected by web applications is **personal data** directly linkable to an individual. Individuals must be informed about what data is collected, how it will be used, and if it will be shared. Users must be given the opportunity to **consent** to collection and storage — this extends even to cookies (with some exemptions).

## 5.1. Data Protection Principles:

UK legislation on personal data processed by computers dates back to the **Data Protection Act 1984**. The **EU Directive 95/46/EC** (1995) set out a framework to protect individuals regarding processing of personal data and free movement of data among member states. This became the **UK Data Protection Act 1998 (DPA)**. In May 2018, the **GDPR** was published and adopted into UK law by a new **Data Protection Act 2018**.

The **GDPR** is directly effective in EU Member States. The **DPA 2018** enacts the GDPR into UK law but includes various **derogations** permitted by the GDPR, resulting in some key differences. The **Information Commissioner's Office (ICO)** monitors and enforces the DPA and GDPR in the UK.

## 5.2. What is Personal Data?

The DPA is concerned with **personal data** — data that can be directly linked to an individual. Web applications must consider what data they collect and how it falls under DPA definitions.

## 5.3. Data Controllers and Data Processors:

The DPA recognises that organisations working with personal data may outsource processing and storage. It distinguishes between:

- **Data controller:** The organisation that determines the purposes and means of processing personal data
- **Data processor:** The organisation that processes personal data on behalf of the controller

Different requirements are imposed on each role, impacting data protection governance.

## 5.4. Trans-border Data Flows:

One goal of Directive 95/46/EC was to ensure data collected in one EU member state could be transferred for processing in another. Transferring personal data outside the EU requires safeguards to ensure comparable protection.

**Safe Harbour:** An early agreement with the USA — any US company registered under Safe Harbour was deemed acceptable to receive personal data from EU member states. Following a complaint about Facebook's transfer of user data to the USA (lodged with the Irish data protection supervisor), **Safe Harbour was invalidated** as it was no longer regarded as offering the required level of protection.

## 5.5. Using Cookies:

HTTP is **stateless** — each request-response exchange is independent. Developers use **cookies** to link multiple requests together (e.g. tracking shopping cart contents). A cookie is a small packet of data sent from the server in response to a request, returned by the client with every new request.

Cookies have been used to **track user browsing habits** and construct profiles, which is of particular concern. Cookie use is governed by **EU Directive 2002/58/EC** and the **UK Privacy and Electronic Communications Regulations (PECR)**.

## 5.6. The GDPR:

Directive 95/46/EC had been in place for over two decades and technology had changed significantly. The EU published **Regulation 2016/679** and **Directive 2016/680** in April 2016. The directive came into force immediately; member states had until May 2018 to implement the regulation.

The **GDPR** has been implemented in the UK by the **Data Protection Act 2018**, tailored to the UK's needs but generally adhering to the GDPR with some extensions. Implementation throughout Europe has had a significant influence on UK companies, especially those operating internationally.

---

# 6. Summary:

**Key concepts covered:**

- **Elasticity** allows rapid expansion and contraction of web deployment capacity in response to demand — no lost requests and minimal underutilisation, unlike traditional fixed-capacity deployments that suffer from over-provisioning and under-provisioning
- **Resilience** measures VM availability by detecting physical host failures and migrating VMs to other hosts; AWS achieves this through multiple availability zones
- **Operational vs Capital expenditure** — the cloud shifts IT spending from CapEx to OpEx, enabling faster project launches (days vs months) and benefiting start-ups and departments with limited capital budgets
- **Cost reduction** is the greatest benefit, with studies reporting TCO savings of $500,000+/year through shared infrastructure, increased server utilisation, and reduced administrative overhead
- **AWS pricing** includes on-demand, reserved instances, and spot instances
- **Security risks** arise from multi-tenancy and shared resources; the only barrier between VMs is the hypervisor
- **Data in transit** is secured through separate networks, Layer 2 isolation (VLANs), HTTPS/TLS, and proxy services for multi-hop channels
- **Data at rest** is secured through encryption (e.g. AES-256 for S3) and Key Management Infrastructure (KMI)
- **AWS shared responsibility model** — AWS secures the global infrastructure; tenants secure their own instances, OS, applications, and firewall configuration
- **Data disposal** is a concern when VMs release memory and disk space back to the shared pool — sanitization is recommended
- **Privacy** and **data protection** are governed by the GDPR (2018) and UK Data Protection Act 2018, enforced by the ICO
- **Personal data** collected by web applications requires user consent for collection, use, and sharing
- **Data controllers** determine purposes of processing; **data processors** process data on behalf of controllers — different legal requirements apply
- **Trans-border data flows** require safeguards; the Safe Harbour agreement with the USA was invalidated
- **Cookies** are governed by EU Directive 2002/58/EC and UK PECR regulations

---