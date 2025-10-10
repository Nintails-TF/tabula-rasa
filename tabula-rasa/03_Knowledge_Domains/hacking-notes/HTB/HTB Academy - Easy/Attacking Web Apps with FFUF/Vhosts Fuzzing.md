---
title: 'Vhosts Fuzzing:'
updated: 2023-07-25T15:20:04.0000000+01:00
created: 2023-07-25T13:32:00.0000000+01:00
---

Filtering:

![image1](../../../../_resources/image1-145.png)

In this case we don't know the size of the Vhosts response, but we do know that the incorrect size is 900. We can filter using **-fs 900**. Now we can repeat the same command:

*ffuf -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u [http://academy.htb:PORT/](http://academy.htb:PORT/) -H 'Host: FUZZ.academy.htb'-fs 900*
![image2](../../../../_resources/image2-117.png)

If we try to view the admin page, we can see the access page, but we get an empty page, **which is different from the default domain so we have a different Vhost.** If we try to access the blog or forum pages we will 404!, this gives us another vector of possible vulnerabilities.

**Remember to access the website we need to:**

1.  **Add the new sub-domains to hosts**
2.  **Use the port number**
    1.  **I.e.** admin.academy.htb:47100

Now we can recursively scan it:

Vhosts VS sub-domains:

Vhosts enables us to perform fuzzing on hidden subdomains. The key difference between the two is that **vhosts** are sub-domains that are on the same server and on the same IP. Such that a single IP could serve two or more websites.

**VHOSTS may or may not have public DNS records.**

In many cases, websites have sub-domains that are not published in public DNS records and if we perform **sub-domain fuzzing** we will only be able to "see" public sub-domains. **Vhosts fuzzing** runs a scan that can check both public and non-public sub-domains and vhosts.

Vhosts Fuzzing:

To scan for vhosts, without adding the whole wordlist to our **/etc/hosts** we will fuzz HTTP headers - more specifically the **Host:** header. We do this by using the **-H** flag within ffuf and using the FUZZ keyword within it:

*ffuf -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u [http://academy.htb:PORT/](http://academy.htb:PORT/) -H 'Host: FUZZ.academy.htb'*

![image3](../../../../_resources/image3-91.png)

We see that all words in the wordlists are returning **200 OK.** We will always get a 200 response, to check that if the Vhost does exist we **should get a different response size.** Since we would be getting the page from the vhosts which will show a different page.

**Fuzzing for other vhosts:**
![image4](../../../../_resources/image4-71.png)

We see that test exists as another Vhost.
