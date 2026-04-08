---
date created: Sunday, February 15th 2026, 12:23:22 am
date modified: Sunday, February 15th 2026, 12:30:50 am
---

# Fort Knox

**Points:** 100
**Description:** Just get the password right
**Source:** <https://fortknox.web.baectf.com/>

# Method:
## Description & Investigation:

You have a form with the input bar as read-only, and the password is hidden within the HTML as: `ultra hax!!!`

## Exploitation:

Use cURL to send data instead:
```Bash
curl -X POST https://fortknox.web.baectf.com/login.php \
  -d 'password=ultra hax!!!'
  
<html>
<body>
<p>The key is: '<b>I think we all learned a valuable lesson today</b>'</p></body>
</html>
```
## Key Takeaways & Remediation:

- Use cURL if you are getting trolled by a form.
