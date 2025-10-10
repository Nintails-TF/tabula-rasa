---
title: "Introduction:"
date modified: Monday, May 27th 2024, 3:54:17 pm
---
# Introduction:

The most important rule of hacking web apps is:
***90% of hacking web applications is enumeration.**

If you can get your hooks onto something, you can learn about a piece of software or tool, but if your enumeration sucks, you won't know where to even begin.

If you are white-hat/grey-hat, most companies will not want you to do any privilege escalation or post exploitation, since you can wreck their systems.

First look for the low hanging fruit, see if people are doing their job correctly. Don't assemble a crane to pick up feather, just pick it up with your hands.

# Enumeration:

## Intro to enumeration:

When performing an engagement, I recommend going through the following path of:
![[Pasted image 20240526155931.png]]

This is for a few reasons:
1) Active enumeration can end-up in you being IP banned, rate-limited, blocked, etc.
2) OSINT and Passive is much more stealthy.
3) OSINT and Passive enumeration of systems, enables you to build up your understanding of what is going on in the system.
4) Production systems can have counter-measures in place for active scanning tools.
5) Anyone can run a tool or a script, not everyone is willing to do through research about a company or organisation.

I would say that the best thing in which you can do, is to SLOWLY scan the whole scope of the target and collect data from passive methods whilst your scans are gathering information.

I mean you could write a suite of scripts that does the following:
![[Pasted image 20240527140142.png]]

For this reason, having an automatic testing suite of active tools which can run all the scripts and tools that you want is very nice, you can configure your tools to run slowly, get a coffee and come back with all your data logged on your system.
## OSINT:

## Passive Enumeration Techniques:
- The [[hacking-notes/hacking-notes/HTB/HTB Academy - Easy/Information Gathering - Websites/Introduction|Information Gathering Module]] by HTB gives a 

## Active Enumeration Techniques:

## Making a testing suite script:


# Exploitation:

## Introduction:

When looking at exploitation we have **publicly known exploits** and **private exploits.** 

Many of the top infosec frameworks all describe types of vulnerabilities seen "out in the wild" and how to remediate them. Examples include:

- [SANS Top 25 Most Dangerous Software Errors](https://www.sans.org/top25-software-errors/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Common Weakness Enumeration](https://cwe.mitre.org/)
- [NIST Special Publication 800-series](https://csrc.nist.gov/publications/sp800)

Mainly, I care about the OWASP Top 10, as it gives you clear steps on what you should test first and foremost.
### [[OWASP Top 10 - 2021]]


# Privilege Escalation:

# Post Exploitation:

