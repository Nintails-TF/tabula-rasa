---
title: Source Code Review
updated: 2022-08-02T21:22:56.0000000+01:00
created: 2022-08-02T17:58:28.0000000+01:00
date modified: Wednesday, July 2nd 2025, 5:12:26 pm
---

## Managing Expectations:

Metrics for code review include how many lines of code need to be looked at traditionally. However KLOC (a thousand lines of code) is often used in code reviews. What is *standard* is 100KLOC per person-week when using static analysis tools.

Static analysis tools help save time but they can have many false positives.

When scoping out a project, looking at the number of files to review can be a good metric to use - obviously the missing case would be huge files. 10 files per day is reasonable for manual review per day.

Manual Review is slower but finds more bugs, using tools is quicker but can miss critical bugs and errors. Manual review works at around 1% of speed but leads to a better result.

The general use of thumb is to use static tools on large projects and manual review on small projects. E.g.

\<100KLOC use manual review with static tool aid
\>100KLOC use static tools with manual aid

Devote most of your manual review on key components of the website/software.
