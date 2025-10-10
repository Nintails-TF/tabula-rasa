---
title: 'Responder:'
updated: 2022-09-22T20:33:19.0000000+01:00
created: 2022-09-10T20:06:48.0000000+01:00
---

When visiting the web service using the IP address, what is the domain that we are being redirected to?:

*We get redirected to unika.htb.*

Which scripting language is being used on the server to generate webpages?

*Using Wappalyzer we find out that php is being used.*

What is the name of the URL parameter which is used to load different language versions of the webpage?:

*Page -*
![image1](../../../../../_resources/image1-59.png)

Which of the following values for the \`page\` parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe":

*Accessing the hosts file is a very common method of checking that **Local File Include** vulnerabilities are possible.*

Which of the following values for the \`page\` parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "minikatz.exe":

*RFI is similar to LFI, but we try to load a file or a program.*

What does NTLM stand for?:

*New Technology LAN Manager.*

Using Responder:

NTLM allows us to authenticate to resources in the active directory domain. It is a single sign-on (SSO) because it allows the user to provide authentication only once at a login. NTLM authentication is done as followed:

1.  The client sends the username and domain name to the server.
2.  The server generates a random string of characters, called the *challenge.*
3.  The client encrypts the challenged with the NTLM hash of the users password and sends it to the server.
4.  The server gets the user's password/password hash.
5.  The server compares the hash received to the hash in the database, if these hashes match then the user is authenticated.

(More on NTLM can be read [here.](https://www.ionos.com/digitalguide/server/know-how/ntlm-nt-lan-manager/))

NTLM terminology:

**Hash Function -** a hash function is a one way function that converts data and returns a fixed size value. This is normally called a hash, digest or fingerprint. They are used to store passwords more securely, as you cannot convert the hash back into the password.

There are attacks that are able to try and recover passwords from hashes. So, servers can store password hashes and when you submit your password to a website or program it hashes the input and checks it against the hash in the database and if they match, you can log in.

**NTHash -** an NTHash is the output of the algorithm used to store passwords on Windows systems in the SAM ([Security Account Manager](https://en.wikipedia.org/wiki/Security_Account_Manager)) database and on domain controllers.

**NetNTMLv2 -** This refers to the challenge and response model described when using responder, So a NetNTMLv2 challenge / response is a string specifically formatted to include the challenge and response.

Responder:

Responder works in many different ways, but in this attack it will setup a malicious SMB server. When the target machine attempts to perform the NTLM authentication to that server, Responder sends a challenge back for the server to encrypt with the users password.

When the server responds, Responder will use the challenge to generate the NetNTLMv2, we then use this to try and guess common passwords using the tool John The Ripper to try and crack the hash and generate the same challenge/response.

Once we run responder and we have it *listening for events* what we need to do is set the page parameter using our web file.

![image2](../../../../../_resources/image2-44.png)

(The IP we use here is the same IP as within the responder settings:
![image3](../../../../../_resources/image3-37.png)
)

This gives us the hash:

![image4](../../../../../_resources/image4-29.png)

Connecting to WinRM:

We will use a tool named Evil-WinRM because we don't have PowerShell on Linux by default.

![image5](../../../../../_resources/image5-19.png)

This allows us to connect to the machine's PowerShell:

![image6](../../../../../_resources/image6-11.png)

Basic PowerShell commands include:

Cd - same as linux
Get ChildItem - equivalent to ls.
Type - same as cat

Using Cd to get to root and then looking through files we eventually find out that the flag is stored in users mike desktop:

![image7](../../../../../_resources/image7-8.png)

![image8](../../../../../_resources/image8-6.png)

Getting the flag:

If a regular nmap scan doesn't give anything meaningful. Make sure to scan all ports, since there may be services on other ports that aren't the top 100 that we can exploit. The crux of this box is exploiting NTLM (New Technology LAN Manager) on windows.

We use the **-p-** tag to do this:

![image9](../../../../../_resources/image9-5.png)

We get the following services:
![image10](../../../../../_resources/image10-3.png)

We already know that port 80 is the http port for webpages, port 5985 is the port for WinRM. Which is Windows remote management protocol; it is used to remotely communicate and interface with hosts, execute commands remotely and monitor and configure servers.

This means that if we are able to exploit this service, that we can get shell access to the host.

Web Enumeration:

Trying to access the site using the IP, redirects us to ***unika.htb*** and gives us a dead page, since our host doesn't know how to find ***unika.htb.*** This web-server is employing name-based Virtual hosting for the web requests.

This means that multiple domain names are being hosted on a single server. Allowing one server to share its resources without all the servers needing to have the same hostname.

For us to bypass this, as an outsider, we need to configure our hosts file to understand what ***unika.htb*** is so it can resolve the address and give us the page. We do this by editing our hosts file in /*etc/hosts.*

Using this command in our terminal, we can quickly add whatever is in the echo statement to our hosts file.

**echo "\[IP\] \[Domain Name\]" \| sudo tee -a /etc/hosts**

This allows us to access the website.

(Note that you will need to do this again after a reboot)

Local File Inclusion Vulnerability:

An LFI vulnerability can be caused when page input is not sanitised. It occurs when an attacker Is able to access a website that is not intended to be an option by the application. Commonly, since means using a path to a file as input in a page parameter.

The attacker can input a ../ string in the page parameter and eventually access sensitive files in the local file system. This also can lead to remote code execution in rare cases.

RFI (Remote File Inclusion) is very similar to LFI but it allows an attacker to load a remote file using protocols like http, ftp, etc.

The reason why LFI is possible here is because include() is used in php without proper sanitation. Allowing an attacker to manipulate the page parameter and allow us to view internal system files.

Responder Commands:

Installing Responder:
git clone <https://github.com/lgandx/Responder>

Running it via python:
sudo python3 Responder.py -I tun0
sudo responder -I tun0

(If this doesn't work, try locate the responder file and move to its directory.

Responder currently doesn't work with python 3.10, so you need to use an older python version like python 3.9 or below.

Simply using:
![image11](../../../../../_resources/image11-2.png)
runs responder just fine.

Decrypting the Challenge:

Now using the John The Ripper tool we can crack this NetNTLMv2 Hash. First we make the hash dump into a text file. Using:

Echo \[hash text\] \> hash.txt

Using **John** we can use a wordlist to see if the password matches the password list. Encrypting each challenge with that password and if the result matches the response, we have the correct password.

![image12](../../../../../_resources/image12.png)

This gives us the password:

**badminton**
