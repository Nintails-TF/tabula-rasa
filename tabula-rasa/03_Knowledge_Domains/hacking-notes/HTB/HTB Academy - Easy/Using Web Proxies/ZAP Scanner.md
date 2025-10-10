---
title: 'ZAP Scanner:'
updated: 2023-08-12T20:48:08.0000000+01:00
created: 2023-08-12T16:58:49.0000000+01:00
---

Spidering:

Firstly, we will want to start crawling through all links on the website, we can do this using the **Spider** tool. We can activate this via locating a request in **History** and clicking **Attack\>Spider.** We can also use the HUD to perform spidering, we can go to the page we want to spider and click the spidering option.

*ZAP will only try to spider to things that are in scope, but when can just automatically add spidered websites into our scope.*

We can see the progress of the spidering via the HUD or looking at the main ZAP UI. Once our scan is complete we can access the sitemap via the ZAP main UI or by clicking **Sites Tree** on the ZAP HUD.

*ZAP has the **AJAX Spider** which can access links that are requested through JavaScript, it is slower than regular spidering but can give us a better output and add a few links that the normal spider could of missed.*

Passive Scanner:

As ZAP spider runs and makes requests to various endpoints, it is automatically using a **passive scanner** on each response to try and find security issues from the source code. This is why we can sometimes see security issues being generated right away.

Remember: **The right pane shows us ALL alerts on the web application, The LEFT pane shows alerts found on the CURRENT page.**

Active Scanner:

Once our site tree is populated, we can click **active scan and we can start an active scan on all pages in scope.** This will try various types of attacks against all identified pages and HTTP parameters to find **as many vulnerabilities as possible.**

As the active scan runs, we will see alerts start to pile up. We can check the ZAP main UI for details on these, in particular we want to look at **high** alerts since they normally end up with **compromising the back-end server or the web app.**

Viewing Alerts:

We can view **high** alerts by clicking on the correct tab in the ZAP hud or by looking inside the ZAP main window. This often tells us how to patch the vulnerability and how to replicate it:

![image1](../../../../_resources/image1-178.png)

We can then look in the **alerts window** to see what request lead to this vulnerability, then we can repeat it.

Reporting:

We can also generate a report using ZAP, by going into the ZAP hud and clicking on generate HTML report or by using the ZAP main interface and going **Report\>Generate HTML Report.**

