---
title: SeedsRoots
date modified: Thursday, May 16th 2024, 4:33:46 pm
---
* * *

## title: Seeds/Roots

updated: 2022-10-19T16:29:03.0000000+01:00  
created: 2022-10-19T15:54:57.0000000+01:00

**ASN Enumeration:**

ASN (Autonomous System Numbers) are given to large networks, they allow us to track some of the IT infrastructure that these companies have, the best way to get this information is via Hurricane Electric's search:

http://bgp.he.net

This allows us to get some AS numbers, they can give us all the known IP's that that company uses. *It doesn't include AWS and Azure environments however.*

You can use ASN on the command line, via **Metabigor** and **ASNLookup**. The only issues with these tools is that you can get the wrong org for say "Tesla" if another org has Tesla in its name.

After we have more of these seed domains, we can scan the **whole** ASN with a port scanner and return any root domains that we see in SSL certificates, we can use **Amass** for this.

The more seeds we have the better.

**Reverse WHOIS:**

Every website has some kind of registration info on file. Two pieces of data we can use are org name and emails inside the WHOIS data.  
A free WHOIS lookup is [whois.com](https://www.whois.com).

You need to take care, since the data can be outdated. It could contain parked domains or redirected out of scope assets. A large company could just be sitting on domains.

**Shodan:**

Shodan is an infrastructure spider on the internet. It is very powerful and contains all sort of information, you need to register for it however. (holy fuck it is expensive too).

https://www.shodan.io/

In reference to seeds/roots in the context of recon. This means the root/seed domains are the highest level domain.

**Acquisitions:**

We can look at Acquisitions to expand our available assets if they are in scope. We can use sites like [**Crunchbase**](https://www.crunchbase.com/home), Wikipedia and Google searches.

You can add these acquisitions to your domains of available seeds *if they are in scope! <u>Make sure to check that the acquisition is still acquired for the top level company.</u>*

**Crunchbase** also gives lots of other good information about companies too.

**Ad/Analytic trackers:**

You can get information about domains and sub-domains by looking at a target's ad/analytics tracker codes. We can look at the relationship file with a Firefox extension named **BuiltWith**.

**Google dorking:**

You can google items like Copyright text, TOS text and privacy policy text to further try to glean information, You can also use certain queries and syntax to get hosts from google.