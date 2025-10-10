---
title: TypoSquatting
date modified: Friday, May 17th 2024, 5:42:48 pm
---

Uh oh! A popular social media site may be the victim of typosquatting. The social media owners might want to fix that so their users don't accidentally go to the wrong site. When does the registration for the `facebooks.com` domain expire? Maybe after it expires, the real company could take control...

Flag format - `byuctf{YYYY-MM-DD}` (ie, `byuctf{1994-12-30}`)
***
We can look up this information using an `whois`search.

```Bash
whois facebooks.com
...SNIP...
Updated Date: 2024-01-12T09:00:09Z
Creation Date: 2004-04-10T20:01:46Z
Registry Expiry Date: 2025-04-10T20:01:46Z
```
