---
title: Active sub-domain enum Task
updated: 2023-08-04T15:34:10.0000000+01:00
created: 2023-08-03T18:59:05.0000000+01:00
date modified: Monday, May 13th 2024, 10:19:29 pm
---

![image1](../../../../../_resources/image1-156.png)
![image2](../../../../../_resources/image2-127.png)

1.  First add this domain to /etc/hosts
2.  Perform a dig scan on the target's IP
    1.  ![image3](../../../../../_resources/image3-98.png)

You can then see the highest-level domain in the answer section:
![image4](../../../../../_resources/image4-77.png)

![image5](../../../../../_resources/image5-59.png)

1.  Using **dig** look at the authoritative section
    1.  ![image6](../../../../../_resources/image6-38.png)

We will see 2 zones - the root and non-root version:
![image7](../../../../../_resources/image7-32.png)

![image8](../../../../../_resources/image8-28.png)

This isn't in the inlanefreight.htb zone, as when we look through the Ips, we don't get a match. So where are these Ips located? We need to check each subdomain in **the lookup.txt** list to check if it **has zone transfers**. We can just modify our earlier script to nslookup and to query all of the subdomains:
![image9](../../../../../_resources/image9-24.png)

**We then can see the Ips from the new internal.inlanefreight.htb zone:**
![image10](../../../../../_resources/image10-19.png)

![image11](../../../../../_resources/image11-14.png)
Looking at the list from the command:
nslookup -type=any -query=AXFR inlanefreight.htb ns.inlanefreight.htb \> lookup.txt

We can find that 10.10.200.5 corresponds us.inlanefreight.htb

To look for TXT records, we need to define the q-type:
![image12](../../../../../_resources/image12-10.png)
This is because when using dig we only see **A** records by default.

1.  Make sure to add the domain **root.inlanefreight.htb** and **ns.inalnefreight.htb** to /etc/hosts
    1.  This means we can look at the name server and use nslookup.
2.  We can look through by defining the **-t TXT** flag in **dig**
    1.  ![image13](../../../../../_resources/image13-9.png)
    2.  (Note that +short here just removes non TXT portion of the dig output. e.g. it only returns double quoted strings).

**Now we need to perform the zone transfer:**
![image14](../../../../../_resources/image14-8.png)

We get tons of name servers:
![image15](../../../../../_resources/image15-6.png)

Now we need to check each zone for TXT records, using the dig command, we will want to automate this. **So creating a bash script that can remove all but the domain names then running a dig check on all of them would return the flag.**

Writing the script:
![image16](../../../../../_resources/image16-6.png)

We collect all of the sub-domain names using:
![image17](../../../../../_resources/image17-5.png)

We can then replace all **Name:** characters with blanks in mousepad. **(There is definitely a better way of doing this).**

**We then create a bash script to check for TXT in the zone and get the flag  
**"ZONE_TRANSFER{87o2z3cno7zsoiedznxoi82z3o47xzhoi}"

![image18](../../../../../_resources/image18-5.png)

To answer this we need to look at all **A (IP address)** records, from both the top-level domain (inlanefreight.htb) and internal.inlanefreight.htb. Using:
![image19](../../../../../_resources/image19-4.png)
We see 19 A records.
![image20](../../../../../_resources/image20-4.png)
SNIP

**If we now look at internal:**
![image21](../../../../../_resources/image21-4.png)
![image22](../../../../../_resources/image22-4.png)
We see 8 A records.

So there are 27 A records across the two zones.
