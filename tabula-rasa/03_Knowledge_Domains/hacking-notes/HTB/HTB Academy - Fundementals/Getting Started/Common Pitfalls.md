---
title: 'Common Pitfalls:'
updated: 2022-12-21T17:04:57.0000000+00:00
created: 2022-12-21T16:56:05.0000000+00:00
---

VPN Issues:

- Am I still connected to a VPN
  - *Check that you have **initialization sequence completed***
- Getting a VPN address
  - *Check our tun0 address using **ip -4 a show tun0***
- Checking routing table
  - *To check connectivity **sudo netstat -rn***
- Pinging gateway
  - *The ping command to see if we have access to a IP, using **ping -c 4 \[ip\]***

Burp Suite Issues:

- Not disabling proxy
  - Make sure that you stop burp when not intercepting requests

SSH Issues:

- Changing SSH key and password
  - Use **ssh-keygen**
  - **Ssh** keys are stored in the .ssh folder by default.

Asking Questions:

![image1](../../../../_resources/image1-86.png)

Answering Questions:
![image2](../../../../_resources/image2-68.png)

