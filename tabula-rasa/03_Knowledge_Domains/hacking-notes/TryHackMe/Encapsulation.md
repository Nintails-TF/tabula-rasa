---
title: Encapsulation
date modified: Wednesday, July 2nd 2025, 5:09:27 pm
---


![image1](../../_resources/image1-231.png)  
As the data is passed down each layer of the OSI model, more information containing specific details is added by each layer.

E.g. The network layer would add data like the source and destination IP address, the transport layer would include info about the specific protocol being used (FTP, HTTP, SMB).

The data link layer is special, in that it adds data to the **end** of the transmission to verify that the data has not been corrupted on transmission. This also increases security as data cannot be intercepted and tampered with (i.e. by using the BURP suite) without breaking the L2 Trailer.

This process is known as encapsulation.

Note that data is given different names during each layer. L4, L3, L2 and L1 use specific names. At the transport layer, data is referred to as a **segments** or **datagrams** depending on if TCP or UDP was used, network layer data refers to these segments/datagrams as **packets**, when this packet of data is passed to the data link layer it becomes a **frame**, finally when it reaches the physical layer it is transferred as a sequence of **bits**.

Once a computer receives the stream of bits, it reverses the process and **de-encapsulates** the data. This is helpful as it allows PCs to have a standardized method of sending and receiving data.

Both encapsulating and de-encapsulating are very important as they are practically used and give a good standard way of sending data. This means that *most other transmissions will consistently follow the same methodology.* This allows different network devices to send requests to other devices regardless of manufacturer, OS or other factors.