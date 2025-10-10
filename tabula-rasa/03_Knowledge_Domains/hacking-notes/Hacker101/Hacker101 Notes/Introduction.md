---
title: Introduction
updated: 2022-08-03T12:01:28.0000000+01:00
created: 2022-08-03T11:39:47.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:12:00 pm
---

Fundamentals:

When working through hacker101, it is important to:

- Be able to run Java apps
- Understand and use web requests (python requests package is good).
  - There are times in which you will want to automate web requests, so this will save lots of time if required.

There are two key tools in completing hacker101 CTFs and in learning using hacker101, those are:

**Burp Suite (Proxy):**

This allows you to watch all HTTP and HTTPS communication, intercept and modify requests and replay existing requests, it is a hugely important tool.

**Firefox:**

Firefox allows you to set proxy settings in the browser instead of system wide, which makes testing easier.

Breaker Mindset:

The goal is to break into applications/websites/servers before anyone else can, so that vulnerabilities can be found, formulate a report and then organisations can use risk management to decide what they want to do with your report of vulnerabilities.

So thinking like an attacker is key. The most important tenant of a hacker is that:

*Pushing a button is the fastest way to figure out what it does.*

If you don't understand how an app works, then you can't really break it apart well.

There is also an imbalance between attacking and defending, the attacker only needs to find a single bug. Whilst the defender needs to remove all (at least the critical) bugs. This means attackers have a big advantage over defenders.
This leads on to the fact that defenders can never find every bug, since they have deadlines and time pressure to build, create and defend systems. Meaning the priority should be given to critical bugs and lower impact bugs should be glossed over. Making an accurate assessment of risk is key to prevent attackers from breaking into and cause real damage.

Goals of Attackers:

Once you know roughly how an app works, you need to have a goal in place. Often the goals of attackers are to steal valuable data that can be monetized (credit cards, crypto, ransom sensitive data). Or they want to cover their tracks (remove data from a monitor server, delete/edit logs).

Reporting:

Each bug should have a report written about it that includes the following:

- Title
- Severity
  - Informational - Issue has no real impact, might have impact in the future
  - Low - Business impact is minimal
  - Medium - Potential to cause harm to users, but not reveal data
  - High - Potential to reveal user data or aids in exploitation of other vulnerabilities
  - Critical - high risk of personal/confidential data exposure, general system compromise, CRE, Malware installation, etc.
- Description
- Reproduction Steps
- Impact
- Mitigation (how is it fixed or stopped)
- Affected assets (generally list of URLs)

