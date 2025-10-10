---
title: DNS
date modified: Sunday, September 1st 2024, 9:29:16 am
---

* * *

## title: DNS  
updated: 2023-08-01T20:28:34.0000000+01:00  
created: 2023-08-01T16:01:47.0000000+01:00

The DNS (Domain Name System) is a great place to look for information about targets, but first we need to understand what DNS is.

What is DNS?:

**The DNS is the internet's phone book.** We use domain names (facebook.com, google.com) to access content on the internet. We use IP (Internet Protocol) to communicate between web browsers and devices. *DNS converts **domain names** into **IP Addresses**.* This enables us to access resources on the internet.

Each device connected to the internet has a unique IP that other machines use to locate it. **DNS** means that we don't need to use **IPv4 (104.17.42.72)** or the modern **IPv6 (2606:4700::6811:2b48)** to go to websites. The advantages of DNS are:

- *It allows names to be used rather than numbers*
- *It is easier for humans to use*
- *By retargeting a name to an new address a server can change its IP without needing to change its name.*
- *A single name might refer to several hosts that can split the workload between servers.*

There is a **hierarchy of names in the DNS structure.** The system's root is unnamed.

We can think about **Top-level domains (TLDs)** as a single shelf of books in a library. The last portion of a hostname is hosted by this nameserver. (i.e. [www.facebook.com](http://www.facebook.com), the TLD server is **com**) Most TLDs have been delegated to county managers who are issued codes, these country codes are managed by a **United Nations** agency.

There are also **generic top level domains** that aren't associated with specific countries or regions, TLD managers have the responsibility for procedures that relate to the \*\*second level domain names (\*\*SLDs) and lower level hierarchy of names.

Nslookup and DIG:

**Nslookup** is a command-line utility that we can use to search domain name servers on the internet so that we can get information on them - the tool has two modes **interactive** and **non-interactive**.

We are able to query **A records** (IPv4) by submitting a domain name. We can also use the **\-query** flag to specify certain resource records (e.g. MX, CNAME, etc). For example:  
![image1](../../../../_resources/image1-151.png)

We can now specify a **nameserver** and **IP** combo to get more info using **DIG:**  
![image2](../../../../_resources/image2-122.png)

- We see the **internet class** (**IN).**
- We know that the information can be held in cache for 282 seconds before another request is made.

Resource Records of DNS:

Resource records are managed by these domain level managers for each country, they have the following structure of:

| **Resource Record** | *A domain name, usually fully qualified, is the first part of the resource record. If a fully qualified domain name is omitted. The **zone name** where the record is located will be added to the end.* |
| --- | --- |
| **TTL** | *The **Time-To-Live** defaults to the minimum value specified in the SOA record (in seconds).* |
| **Record Class** | *This can be Internet, Hesiod, or Chaos. Hesiod is used for grouping data in your DNS and Chaos is used in the Chaosnet, which is a rare network implementation.* |
| **SOA** | *The **Start of authority** is a file that indicates the start of a zone. Each zone has a single SOA record and it contains zone values like serial numbers and timeout information.* |
| **Name Servers** | *The distributed database of DNS is bound by the **NS records.** These manage the zone authoritative name server and the authority of child zones.* |
| **IPv4 address (A)** | *The **A** record is used to map between a hostname and IP address. Forward zones are those with an **A** record.* |
| **Pointer (PTR)** | *The pointer record is the mapping between an IP and the hostname. Reverse zones are those with a pointer record. (inverse of A).* |
| **Canonical Name (CNAME)** | *This is the alias that is mapped to an **A** record using the **CNAME.*** |
| **Mail Exchange (MX)** | *The **MX** record identifies a host that accepts emails. A priority value is given to this host. Multiple MX records can exist on the same host and a prioritized list is made consisting of these hosts.* |

Queries Records - Syntax:

To query A records:  
![image3](../../../../_resources/image3-94.png)  
![image4](../../../../_resources/image4-73.png)

To query PTR records:  
![image5](../../../../_resources/image5-56.png)  
![image6](../../../../_resources/image6-37.png)

To query ANY records:  
![image7](../../../../_resources/image7-31.png)  
![image8](../../../../_resources/image8-27.png)

*(Note that we may not receive an **ANY DNS request** since the have been abolished by RFC8482 - this is because the IETF has stated that they are insecure).*

To query TXT records:  
![image9](../../../../_resources/image9-23.png)  
![image10](../../../../_resources/image10-18.png)

To query MX records:  
![image11](../../../../_resources/image11-13.png)  
![image12](../../../../_resources/image12-9.png)

Determining Provider:

We can gather **A, NS, MX, CNAME** with nslookup and dig. Orgs are given IP addresses on the internet aren't always the owners of said IP - ISPs may lease smaller netblocks to them.

We can gather information with nslookup and WHOIS to get details about if the target is using hosting providers or not.  
![image13](../../../../_resources/image13-8.png)  
![image14](../../../../_resources/image14-7.png)