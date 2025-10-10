---
title: Service Scanning
updated: 2022-08-31T19:01:56.0000000+01:00
created: 2022-08-23T13:04:15.0000000+01:00
date modified: Monday, May 13th 2024, 10:29:27 pm
---

Nmap:

The most basic Nmap scan simply using:

![image1](../../../../_resources/image1-70.png)

(By default Nmap only scans the 1000 most common ports.)

![image2](../../../../_resources/image2-52.png)

**Port** shows us the open ports along with the type of port (TCP or UDP). Note that Nmap only does TCP scanning unless asked to perform a UDP scan.

**State** confirms that these ports are open. Sometimes these ports can be **filtered** meaning that a firewall is only allow access from certain addresses.

**Service** tells us the service name that is running at the port number. However, the default scan will not tell us what is listening on the port. I.e. SSH **normally** runs on port 22, but until we investigate the port, we don't know for certain.

We know that port 3389 is the default port for remote desktop services and is a excellent indication of a Windows machine, whilst port 22 indicates that Linux/Unix based system is running - windows can also be configured to run port 22 though.

Attacking Network Services:

**Banner Grabbing:**

Often a service will look to identify itself by displaying a banner once a connection is started. Nmap can be used to grab banners by using:

nmap -sV --script=banner \<target\>

But we can also just use netcat (nc):

![image3](../../../../_resources/image3-44.png)

We can automate this using Nmap:

nmap -sV --script=banner -p21 10.10.10.0/24

SMB:

SMB (Server Message Block) is a widespread protocol used on Windows machines that allow for vertical and lateral movement. Sensitive data like credentials can be found in network file shares, certain versions of SMB can also be vulnerable to RCE exploits.

It is important to enumerate this sizeable attack vector carefully. In Nmap you can use scripts like smb-os-discovery.nse, to extract information about the reported OS version.

![image4](../../../../_resources/image4-36.png)

We can use metasploit with EternalBlue modules to exploit this system and we can scan port to check what it is running.

![image5](../../../../_resources/image5-26.png)

We find that our target machine is:

- Running Samba 4.6.2
- Is using a Linux kernel
- It has a hostname of GS-SVCSCAN (Not shown here)
Beginning Exploration of Machines:

Now we are able to start actually exploring a machine. The first step in exploring a machine is to:

*Identify the operating system and any available services that might be running.*

A **service** is an application that runs on a computer that performs useful functions for other users or computers. We call these specialised machines **servers** as they provide users with resources by interacting with them.

Now, what we are interested in is if these services have been misconfigured or have a vulnerability. So that we can exploit them to gain some sort of access or achieve an objective, like destroying data or something like that.

Computers have an assigned **IP address**, which allows them to be uniquely identified and accessible on a network. The *services* running on these computers can be assigned a *port number* that makes the services accessible (like HTTP, HTTPS, SSH, SMB).

We know that port numbers range from 1 to 65,535 with the most important and well known ports occupying ports 1-1023 as they are **privileged services.** Port 0 is reserved in TCP/IP networking and is not used in TCP and UDP messages.

***If anything tries to bind to port 0 (like a service), it will bind to the next available privileged service.***
I.e. it is a wild card port.

To access a service remotely we need to connect using the correct IP address and port number and use a language that the service can understand. Tools have been created to scan these ports the most popular being **Nmap.**

Advanced Nmap:

We can use different parameters in Nmap to obtain more detailed information.

- -sC: Nmap will try to give more information by running default scripts.
- -sV: Nmap will fingerprint services on the target system and identify the service protocol, app name and version.
- -p-: Nmap will scan all ports. (All 65535 TCP ports).

After you gain information from Nmap, you should note what is running and the version of what is running, older software is generally more vulnerable and is often unsupported.

Nmap scripts:

There are times in which we will want to run specific scripts to check for vulnerabilities. These can be run by using:

**nmap --script \<script name\> -p\<port\> \<host\>**

FTP:

The File Transfer Protocol (FTP) often contains interesting data, we can use nmap to scan port **21**.
![image6](../../../../_resources/image6-17.png)
We then can see that vsftpd 3.0.3 is installed and we can anonymously access the pub directory.

We can then connect to the FTP command line utility:

![image7](../../../../_resources/image7-14.png)
and navigate it for files.

- Ls to display directories
- Cd to change directories
- Get to download files.
- Exit to leave

Shares:

SMB allows users and admins to share folders and make them accessible remotely by other users. These shares can have sensitive details like passwords. We can use smbclient to interact and enumerate these systems.

- -L specifies we want a list of available shares on the host
- -N suppresses the password prompt.

![image8](../../../../_resources/image8-12.png)

We can see the non-default share of users. We can attempt to connect to this share as a guest or we may need credentials to proceed.

SNMP:

SNMP community strings often provide information and stats about devices or routers, helping us gain access to it. The manufacturer community strings of public and private are often unchanged. In SNMP versions 1 and 2c access is controlled by a plaintext community string that if we know, we can gain access.

In SNMP version 3 there is encryption and authentication. Examination of process parameters can lead to finding and reusing passwords for other environments in the organisation. **Snmpwalk** can be used to achieve these goals.

![image9](../../../../_resources/image9-11.png)
![image10](../../../../_resources/image10-9.png)

Open source tools like <https://github.com/trailofbits/onesixtyone> can be used to brute force common community strings.

![image11](../../../../_resources/image11-8.png)
