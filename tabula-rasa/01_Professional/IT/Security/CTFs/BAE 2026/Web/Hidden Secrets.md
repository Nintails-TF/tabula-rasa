---
date created: Sunday, February 15th 2026, 1:28:30 am
date modified: Sunday, February 15th 2026, 1:38:37 am
---

# Hidden Secrets

**Points:** 250pts
**Description:** Can you find the hidden information?
**Source:** <https://hiddensecrets.web.baectf.com/>

# Method:
## Description & Investigation:

We are given a blank page with the phrase: `Nothing to see here.` Inspecting the source, hints at robots `<!--  Hopefully those pesky robots will leave us alone -->`

## Viewing Robots.txt + Access Super Secret:

```txt
# These mustn't be crawled!
User-agent: *

Disallow: /tmp
Disallow: /super_secret_access_instructions
```

I think I know where I'm going, 

The URL (<https://hiddensecrets.web.baectf.com/super_secret_access_instructions/>), states that: Only people using the **Super Secret Web Browser** can get to the real site!

Using cURL:
```
curl -A "Super Secret Web Browser" https://hiddensecrets.web.baectf.com/

<html>
<body>
You're a winner! The key is <b>Do Androids Dream Of Highly Fragmented Sheep?</b>
</body>
</html>
```
## Key Takeaways & Remediation:

- Don't jerry rig technology into being access control when it shouldn't be.
	- Don't use User-Agents for authentication
		- Users can just change them easily,
	- Robots.txt is public and is used for guiding crawlers.
		- User can read them publicly.
