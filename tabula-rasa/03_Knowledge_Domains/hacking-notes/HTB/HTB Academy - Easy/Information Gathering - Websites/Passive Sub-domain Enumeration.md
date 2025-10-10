---
title: Passive Sub-domain Enumeration
updated: 2023-08-02T08:49:21.0000000+01:00
created: 2023-08-01T20:34:30.0000000+01:00
date modified: Monday, May 13th 2024, 10:19:45 pm
---

Formatting certificate requests:

We can format a certificate request into a text file with JSON formatting like so:

***export TARGET="facebook.com"***
***curl -s "[https://crt.sh/?q=\${TARGET}&output=json](https://crt.sh/?q=$%7bTARGET%7d&output=json)"\|jq -r '.\[\] \| "\\(.name_value)\n\\(.common_name)"'\|sort-u \>"\${TARGET}\_crt.sh.txt"***

Where:
![image1](../../../../_resources/image1-152.png)

We then can read the file using **head** or **cat:**

***head-n20 facebook.com_crt.sh.txt***

(This would give us the first 20 names).

**Alternatively we can use OpenSSL to perform the same action:**

**export TARGET="facebook.com"**
**export PORT="443"**
**openssl s_client -ign_eof 2\>/dev/null \<\<\<\$'HEAD / HTTP/1.0\r\n\r'-connect "\${TARGET}:\${PORT}"\|openssl x509 -noout -text -in - \|grep'DNS'\|sed-e 's\|DNS:\|\n\|g'-e 's\|^\\\*.\*\|\|g'\|tr-d ','\|sort-u**

Automatic Passive Subdomain Enumeration:

Now that we are able to manually get data like sub-domains, TLDs, IP ranges, etc. We can automate the process using tools or by making our own tools.

**TheHarvester** is a good tool to use that is simple and powerful - it is used to collect information on a company's attack surface. The tool collects **emails, names, sub-domains, IP addresses** and **URLs** from public sources. Some example of modules that exist are:
![image2](../../../../_resources/image2-123.png)

**To automate this,** we create a text file with the modules we want to use:
![image3](../../../../_resources/image3-95.png)

Introduction:

**Sub-domain enumeration** refers to mapping all available sub-domains within a domain name. The reason why we perform this is to increase our attack area and to uncover assets used by admins/management that are "hidden" via **security by obscurity.**

Doing this passively means that we are going to be using **third party services** and **public information**.

Virus Total:

[VirusTotal](https://www.virustotal.com/gui/home/upload) is a *DNS replication service* which preserves DNS resolutions made when users access the URLs of the website. To look at info about a domain we need to look at the **relations tab.** (*Make sure you look up a search not a URL.)*
![image4](../../../../_resources/image4-74.png)
You will get a ton of information you can use.

Certificates:

Another interesting source of information we should look at is **TLS/SSL certificates**. This is because of **Certificate Transparency** (CT) requires every SSL/TLS certificate that is issued by a Certified Authority needs to be publicly accessible.

Popular resources for doing this are:

1.  <https://censys.io>
2.  <https://crt.sh>

*Crt.sh will be our primary resource, since censys is more corporate.*
![image5](../../../../_resources/image5-57.png)
The data is good, but we want to format this data in a more readable manner.

TheHarvester syntax:

**export TARGET="facebook.com"**
**cat sources.txt \|while read source ;do theHarvester -d "\${TARGET}"-b \$source-f "\${source}\_\${TARGET}";done**

*To sort this:*
**cat\*.json \|jq -r '.hosts\[\]'2\>/dev/null \|cut-d':'-f 1\|sort-u \>"\${TARGET}\_theHarvester.txt"**

Merging all files:

**cat facebook.com\_\*.txt \| sort-u \> facebook.com_subdomains_passive.txt**
**cat facebook.com_subdomains_passive.txt \|wc -l**

***OSINT: Corporate Recon goes more in depth on getting information like this.***

