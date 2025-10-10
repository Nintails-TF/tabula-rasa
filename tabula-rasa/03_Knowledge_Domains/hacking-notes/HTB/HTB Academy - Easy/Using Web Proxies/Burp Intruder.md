---
title: Burp Intruder
updated: 2023-08-12T13:02:18.0000000+01:00
created: 2023-08-11T11:24:20.0000000+01:00
date modified: Monday, May 13th 2024, 11:01:08 pm
---

Introduction:

Both BURP and ZAP provide important tools that are essential for web app testing beyond general web proxy usage, those being **web fuzzers** and **web scanners.**

Burp has a web fuzzer called **Burp Intruder** which can be used to fuzz pages, directories, sub-domains, parameters, parameter values and many other pieces of information. It is lots more advanced than most CLI tools, but it is capped at 1 request per second in the community version, **unlimited speed in the pro version**.

This makes the **pro version** of burp one of the best web fuzzers around.

Target:

First we should start up Burp as normal and start our proxy and send the request we want to fuzz **Burp intruder** we can do this via a right-click interact or using **CTRL+I**. We can use **CTRL+SHIFT+I** which will take us to the intruder panel:
![image1](../../../../_resources/image1-175.png)
*Fig 1.1 - Our target, these details will be copied from request we sent to intruder.*

Positions:

The second tab, **positions** is where we will place our **payload position pointer**, this is the point in which our wordlist will be placed and the fuzzer will iterate over. This is similar to CLI tools like FFUF or GoBuster.

To check if a web directory exists, our fuzzing should be in **GET /DIRECTORY/** so that pages that exist will give us the **200 OK** response code - Otherwise we will just get 404s. So we need to select the **DIRECOTRY** as our payload position. Either by wrapping it in **§** or by highlighting the word and adding the § symbol:
![image2](../../../../_resources/image2-144.png)
*Fig 1.2. Setting the DIRECTORY tag in the HTTP request header.*

(The directory name in this case can be anything and can be used to refer to each pointer, this is helpful when we want to use multiple wordlists).

Finally, we have an option called **attack type**, this defines how the payload pointers are used and determines which payload is at which position. The **Sniper** attack only uses one position.

*Make sure to leave 2 empty lines at the end of the requests to avoid server errors.*

Payloads:

The third tab, we configure our payloads, we get to choose and customise our payloads and wordlists. This is what is going to be iterated over. The four main things we are going to configure are:

1.  Payload Sets
2.  Payload Options
3.  Payload Processing
4.  Payload Encoding

**Payload Sets:**

This is the payload number and attack type, we can configure the number of payloads we wish to use:
![image3](../../../../_resources/image3-110.png)

For a sniper attack, we only attack with 1 payload, but other types of attacks like the **cluster bomb** attack requires several payloads.

Next we need to configure payload type, this is the type of wordlists/payloads that we are using, Burp uses a variety of **Payload Types** each of which act in different ways:

- **Simple list**
  - *The most basic and fundamental type, we provide a wordlist - typically a txt - and intruder will iterate every line.*
- **Runtime file**
  - *Similar to the simple list, but loads line-by-line to avoid excessive memory usage by Burp.*
- **Character substitution**
  - *Enables us to specify certain characters and their replacements - then Burp will try all possible permutations.*

There are also many other payload types which can be used - many of which aid in the creation of a **custom wordlist.**

Attack:

Now that we have everything configured we can launch the attack. Importantly, all lines that started with **.** Are skipped.

**Burp Intruder** can be used to perform any web fuzzing or brute-forcing; brute forcing passwords, PHP parameters and more. Even password spraying in active directory environments. Such as OWA, SSL VPN portals and RDS services.

The free version sucks dick though.
Payload Options:

Next, we must specify the **Payload Options,** for a simple list we need to pick a wordlist or create a custom wordlist.

We can use the wordlist of: **SecLists/Discovery/Web-Content/common.txt** in this exercise.
![image4](../../../../_resources/image4-87.png)

We are able to add multiple wordlists or manually add a few strings we think could exist on the target TLD (Top level domain).

*Do note that **runtime file** is better for very large lists rather than **simple list.** Since you can get memory throttled using simple lists.*

Payload Processing:

Another option we can apply is **payload processing**, which enables us to determine fuzzing rules over the loaded wordlist. So if we wanted to add a file extension to search for (.php, .js, .html, etc) or we wanted to filter on a specific critera.

We can also add rules to skip certain lines, We can use **regex** to provide a regex pattern to skip:
![image5](../../../../_resources/image5-67.png)

We can then check the payload processing tab to check that our rule is enabled and that it has been added:
![image6](../../../../_resources/image6-45.png)

Payload Encoding:

The final option we have in **burp intruder** is the option to **encode** the payload, we can URL encode certain characters that may be picked up by an IDS or WAF:
![image7](../../../../_resources/image7-39.png)

Options:

We can configure many options in this tab or simply use default parameters, e.g. we can set **retired on failure** and **pause before retry** to 0.

Another very helpful option would be the **Grep - match** feature, which enables us to flag specific requests - so we could highlight webpages that return the **200 - OK** code:
![image8](../../../../_resources/image8-33.png)

We will also want to **disable** *Exclude HTTP headers* **since we may find important details inside the HTTP header.**

We can also use the **Grep - Extract** feature which is useful if the HTTP responses are lengthy and we only care about a certain portion of the response.

*The **resource pool** tab specifies how much of our network resource we can allocate to intruder, this is very helpful in large attacks, but is unnecessary for this module.*

Task:
![image9](../../../../_resources/image9-28.png)

We can follow the rules that we have listed here, but to look for file extensions, we have 2 ways of doing this:

1.  Using payload processing to include the suffix HTML:
    1.  ![image10](../../../../_resources/image10-23.png)
2.  Adding the a precision pointer in our request:
    1.  **admin/ §1§.html / HTTP 1.1**

This does work on the free version but it is **PAINFULLY SLOW** - you can just use ffuf LOL, the directory that has the flag is 2010.html

HTB{burp_1n7rud3r_fuzz3r!}
