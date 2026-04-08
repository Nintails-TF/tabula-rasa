---
date created: Sunday, February 15th 2026, 12:51:03 am
date modified: Sunday, February 15th 2026, 1:24:53 am
---

# Up Up and Away You Go

**Points:** 200 
**Description:** Login as John to get the key 
**Source:** [https://upupandawayyougo.web.baectf.com/](https://upupandawayyougo.web.baectf.com/)

# Method:

## Description & Investigation:

We are brought to the website `DynaMow Design`, a template site with various sections. Most interestingly it has a user login page and a forgotten password form that requires a username, full name, and phone number. Pages are loaded dynamically via a `?page=` parameter (e.g. `?page=about`, `?page=login`), suggesting server-side file inclusion.

## Enumeration:

### Discovering the File Inclusion

The `?page=` parameter maps directly to a PHP `include()` call. Requesting a non-existent page reveals an error:

```
Warning: Include file doesnotexist does not exist
```

This confirms the server is including files based on user input. Testing directory traversal with `../../../etc/passwd` initially failed, but an HTML comment in the error response leaked the content root:
```html
<!-- Raw '/var/etc/passwd', Root: '/var/www/html/content' -->
```

Pages are served from `/var/www/html/content/`, meaning we need to traverse four levels up to reach the filesystem root (content → html → www → var → /).
### Reading /etc/passwd

```bash
curl 'https://upupandawayyougo.web.baectf.com/?page=../../../../etc/passwd'
```

This returned the full passwd file. The field for the `john` account contains exactly the information the password reset form requires:

```
john:x:1001:1001:John Wilson,Room 111,0207 946 0871,:/home/johnw:/bin/bash
```

- **Username:** `john`
- **Full name:** `John Wilson`
- **Phone number:** `0207 946 0871`

## Exploitation:

With John's details extracted, the forgotten password form can be submitted to reset his password and retrieve the key.

## Key Takeaways & Remediation:

- User-controlled parameters passed to `include()` or `file_exists()` should be validated against a whitelist of allowed pages, never used directly for filesystem access.
- The GECOS field in `/etc/passwd` is world-readable and can contain sensitive personal information (full names, room numbers, phone numbers). These fields should not be used as security questions or password reset verification.
- Error messages and HTML comments leaked the content root path, making it trivial to calculate the correct traversal depth. Production servers should suppress detailed error output and never include debug comments.