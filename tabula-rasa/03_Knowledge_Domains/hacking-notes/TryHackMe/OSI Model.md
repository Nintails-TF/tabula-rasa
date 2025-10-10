---
title: OSI Model
updated: 2022-09-20T21:14:14.0000000+01:00
created: 2022-09-20T20:47:42.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:10:56 pm
---

![image1](../../_resources/image1-230.png)
OSI Model:

The OSI (Open System Interconnection) model is a standardized model used to show how computer networking takes place. In reality, It is more the TCP/IP model that real-world networking uses, but the OSI model is a good place to start at.

The OSI model has 7 layers:

**Application (Layer 7):**

The application layer provides networking options to programs running on the computer. It works almost exclusively with applications. Providing them with a way of transmitting data to the *presentation* layer.

**Presentation (Layer 6):**

The presentation layer receives data from the application layer. This information that it receives needs to be interpreted into a standard form (Like how programming languages are converted into machine code). So that code can be understood by the receiving computer.

The presentation layer handles this interpretation and is also able to handle encryption, compression and other transformations on data.

**Session (Layer 5):**

After the presentation layer formats the data, the session layer checks to see if it possible to make a connection with the other target computer in the network. If it can't then it sends an error message and the process stops.

However; if a connection can be made, the session layer is responsible to maintain that connection between computers.

The session layer is important as it allows multiple requests to be made to different end points at once without mixing up data. After the session layer logs a connection between a host and a remote computer the data is passed to the transport layer.

**Transport (Layer 4):**

The Transport layer is used to actually send the data between computers. It first chooses which protocol to transfer data over (TCP/UDP).

The transport layer divides these transmissions of data into pieces/packets (TCP calls these **segments** whilst UDP calls these **datagrams**.)

**Network (Layer 3):**

The network layer is responsible for locating the destination of your request. i.e. the internet is just one huge network. When you try to request a webpage, the network layer handles this.

It tries to find the best route to take. Currently in this example, we are using *logical* addresses (IP addresses). The most common type of logical addressing the IPV4 format (even though we ran out of them).

**Data Link (Layer 2):**

The data link layer focuses on the physical addressing of the transmission. Meaning when it receives a packet of data from the IP address of the computer and adds the MAC address of the endpoint.

Inside every network enabled computer there is a NIC (Network Interface Card) which comes with a unique MAC (Media Access Control) address to identify it.

These MAC addresses are set by manufactures and are literally burnt into the cards, so you can't change them, *but you can spoof them.*

Finally, the data link layer presents data in a suitable format for transmission and checks received data to make sure that it hasn't been corrupted during transmission.

**Physical (Layer 1):**

The physical layer relates to the hardware within a PC. It is the job of the physical layer to convert binary data of the transmission into signals then transmit them over the network.

It is also responsible for receiving signals and converting them back into binary.
