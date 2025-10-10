---
title: Basic Tools
updated: 2022-09-09T09:36:06.0000000+01:00
created: 2022-08-21T03:05:36.0000000+01:00
---

Netcat:

Also known as ncat, nc. Netcat is a powerful network utility that allows us to interact with TCP and UDP ports. It has many purposes in a pen test, though primarily it is used to connect to shells.

Additionally, Netcat is used to connect to **any listening port** and interact with the service running on said port. For example, if SSH is programmed to handle connections over port **22** to send data and keys, we can use Netcat to connect to port 22.

![image1](../../../../_resources/image1-69.png)

We can see that port 22 send us a *banner,* showing us that SSH is running on it. This technique is called **Banner Grabbing** and it helps us figure out what service is running on a particular port.

Netcat is also able to be ran on windows PowerShell and is able to transfer files between machines.

**Socat** is a similar network utility which has a few features that plain Netcat doesn't. Like forwarding ports, connecting to serial devices and upgrading a plain shell to a TTYs over TCP connections (<https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/#method-2-using-socat>)

Basically, we are able to make our reverse shell more stable by using **Socat**.

Vim:

Vim or Vi is a text editor used to write code and edit text files on Linux systemcs. It has the benefit of only requiring the keyboard to be used. So that once you learn it, it can boost productivity and efficiency when writing code.

Vim or Vi is also installed on most Linux systems, so If you compromise one, you can write code easily on it and edit files. There are also many plugins that you can install to extend the usefulness of Vim.

Vim cheat sheet: <https://vimsheet.com/>

Important Vim commands:

- Creating a new file is done by inputting a new file name.
- You start in normal mode by default and to write and edit the file you need to hit **I** to enter *insert mode*.
  - Esc can be used to leave insert mode and go back to normal mode.
- : is used to enter *command mode*

Optional Exercise:

![image2](../../../../_resources/image2-51.png)
We simply use netcat with the following parameters to *banner grab* the server.

![image3](../../../../_resources/image3-43.png)

Certain Tools are essential to working in infosec or as being a hacker. Those being **SSH, Netcat, Tmux** and **Vim.**
These tools are not intended to be pen testing tools, but are critical in the penetration testing process.

SSH:

Secure Shell (SSH) is a network protocol that runs on port **22** by default. It provides users like admins with the ability to connect to a computer remotely. SSH can be configured with password authentication using **public key authentication.**

**SSH** enables us to remotely access other systems on the same network, facilitate connections to other resources in other networks by using port forwarding and proxying and allows us to upload and download files to and from remote systems.

SSH uses a client-server mode, a client must run an *ssh application* like OpenSSH to an SSH server. When attacking a system, we often are able to obtain cleartext credentials or an SSH private key that can be leveraged to connect directly to a system via SSH.

SSH connections are much more stable than reverse shells and can be used to *jump Hosts* to enumerate and attack other hosts in the network, set up persistence and transfer tools. If we gain credentials we can use SSH to login remotely to a server using the following

![image4](../../../../_resources/image4-35.png)

Tmux:

Terminal multiplexers, like **tmux** and **Screen** are great for expanding a standard Linux terminal's features. Like having many windows within a single terminal and jumping between them. Tmux can be installed by using:

Sudo apt install tmux -y

The key commands for using tmux are:

- **CTRL + B -** Is used to prefix and tmux commands.
- **C -** Is used to create a new window
- **SHIFT + % -** Is used to split windows vertically. (0, 1, 2, etc can be used to access each window number)
- **SHIFT + " -** Is used to split windows horizontally. (you can also use the arrow keys to navigate terminals.)

*<https://tmuxcheatsheet.com/> and [Introduction to tmux](https://www.youtube.com/watch?v=Lqehvpe_djs) are both useful resources to learn more.*

![image5](../../../../_resources/image5-25.png)
