---
title: 'Burp Scanner:'
updated: 2023-08-12T16:58:43.0000000+01:00
created: 2023-08-12T14:09:43.0000000+01:00
---

Introduction:

An essential feature of burp suite is the **Burp Scanner**, as it scans for various web vulnerabilities using a **crawlers** for building the website structure and a **scanner** for active scanning.

**Burp scanner is a pro feature** and you cannot use it in the free community version - however since it is a tool that is used in many enterprises, it is expected to be a paid feature.

Target Scope:

To start a scan in **burp suite** we have the following options:
1.  Start scan on a specific request from our proxy history
2.  Start a new scan of a set of targets
3.  Start a scan on a list of items in-scope

**Proxy history:**

To scan a target on our proxy history we can right click and either perform an **active/passive** scan, this will start a scan with the default configuration:
![image1](../../../../_resources/image1-177.png)

**Starting new scan:**

We can navigate to **new scan** on the dashboard tab which will allow us to configure a new scan on a set of custom targets. Instead of creating a scan from scratch we can define the scoping tool. The **target scope** will allow us to select what we include/exclude in our scans.

Burp also enables us to only scan what is in-scope so we save resources and avoid targeting stuff that is out of scope as defined in rules of engagement.

If we go to **Target\>site map:**
![image2](../../../../_resources/image2-146.png)
We see a list of all files and directories that burp has detected through its proxy. We can add an item to scope by right clicking on it and adding it to scope:
![image3](../../../../_resources/image3-112.png)

We can also go to the scope tab and add or remove items from scope, we can also exclude any items that will end our session - like a logout function. Furthermore, we can also scan using advanced regex functions:
![image4](../../../../_resources/image4-89.png)

Crawler:

Once we have our scope we can access the **Dashboard** tab and we can start a **new scan.** Which will be populated with anything in scope:
![image5](../../../../_resources/image5-69.png)

Once we have started a scan, we can start **crawling.** A web crawler navigates a website by accessing any links that are found on a page, accessing forms and examining any requests that are made so it can build a comprehensive map of the website.

Burp scanner can also run a **Crawl and Audit** which will crawl a website then perform a scan on the targets.

*Note that crawling tools only follows and maps links found on the page - there can still be links that aren't reference on the page that we can fuzz and uncover.*

When we first start to crawl we can either **build a custom configuration** or **Select a preset from a library.** Selecting from library is the simpler solution:
![image6](../../../../_resources/image6-47.png)

When crawling we can give our crawler some credentials so that they can try to login and look at directories that only authenticated users can access - in the scope of this module - we don't need to.

Once crawling is completed we can click on the **view details** button get more details about the scan. We can also look at the **Site Map** of the target and view the newly found resources:
![image7](../../../../_resources/image7-41.png)

Passive Scanner:

Now that we have a populated sitemap, we can scan for vulnerabilities. We have two methods of scanning **Passive or Active vulnerability scanning.**

A **passive scan** will not send any requests to any of the webpages and will identify **potential vulnerabilities** by looking at source code. Burp Scanner has a level of **confidence** which it assigns to each vulnerabilities.

A passive scan can be done by right-clicking the sitemap and clicking **Do passive scan.**

*A passive scan gives us a good place to start looking.*

Active Scanner:

An **active scan** is the more powerful scan, as it runs a powerful scan that checks a whole host of possible vulnerabilities and verifies them. Burp Scanner is also updated frequently to recognise new vulnerabilities.

We can right-click a sitemap then click **Do active scan**. Note that this will take far longer than a passive scan, as a scan is running we can click on view details and look at the **logger.**

Once a scan is done, we can look inside the **Issue Activity** tab to see all of the issues - we can also filter and look for **High** vulnerabilities that are **Certain.** So that we only see results for attacks that are important.

Reporting:

We can use Burp to generate a report by going to **Issue\>Report issues for this host** which will create a summary on vulnerabilities that it has found:
![image8](../../../../_resources/image8-35.png)

Burp's report also shows some POC details on how to exploit the vulnerability. This kind of report is often used as **supplemental information** when talking with clients or organisations.

These reports are not comprehensive, but can help with appending information and help with remediation and tracking.

