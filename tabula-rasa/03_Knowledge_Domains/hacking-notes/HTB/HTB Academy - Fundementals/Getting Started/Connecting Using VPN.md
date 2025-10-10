---
title: 'Connecting Using VPN:'
updated: 2022-08-31T19:01:50.0000000+01:00
created: 2022-08-16T10:54:51.0000000+01:00
---

![image1](../../../../_resources/image1-68.png)
VPNs (Virtual Private Networks) allow us to connect to a private network and access hosts and resources as if we were directly connecting to the target private network. VPNs allow us to have a degree of privacy and security, along with preventing eavesdropping.

VPNs work by routing our connecting device's internet connection through the private server in the VPN instead of our ISP. When connected to a VPN the data originates via the VPN server and its public IP address instead of your public IP address.

Client-based VS SSL VPN:

**Client-based VPNs** refer to software to establish the VPN connection, once connected the user's host will work similarly as if connected to a company network and a client will be able to access any resources (apps, hosts, subnets, etc).  

**SSL VPNs** refer to connections between the browser and an SSL VPN gateway and can be configured to only access applications like email and intranet sites or even over an internal network without the need to install software.

Why use a VPN?:

We can use VPN services to connect a VPN server in another part of the country or world, obscuring our browsing traffic and public IP address. Still, as long as we connect to a company server there is a chance that data is being logged or that the VPN service is not following good security practices.

**Using a VPN does not guarantee anonymity or privacy**. But it is useful for bypassing certain network/firewall restrictions - like wi-fi at an airport.

When connecting to target networks we should consider the networks to be *hostile*. As in, that we should only connect to them via a VM and:

- Disable password authentication if SSH is enabled on our attacking VM
- Lockdown any web servers
- Don't leave sensitivity information on our attack VM.
  - Use a separate VM if dealing with client assessments.

