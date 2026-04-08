---
date created: Sunday, February 15th 2026, 1:56:04 am
date modified: Sunday, February 15th 2026, 2:19:44 am
---

# Factxory Reset

**Points:** 400pts 
**Description:** Find a way to login and get the key 
**Source:** [https://factxoryreset.web.baectf.com/](https://factxoryreset.web.baectf.com/)

# Method:

## Description & Investigation:

We are presented with a login form. The HTML source contains a commented-out JavaScript "secure" password system that performs client-side authentication. The script validates a username and password by computing multiplicative and additive checksums over their character codes and comparing against hardcoded target values.

```js
// If the username and password are correct
if(usercode == 1172188274400 && passcode == 1842055687879732800 && usertot == 1537 && passtot == 393644)
```

A comment boasts: _"Recovering the password is going to involve factoring really big numbers - which as any cryptographer knows isn't trivial ;-)"_

## Enumeration:

### Recovering the Credentials

Both `usercode` and `passcode` are products of character codes (each in the range 97–122, i.e. lowercase a–z). Factoring these "big numbers" into their prime components and mapping them back to valid character codes reveals the candidate characters.

**Username** (`usercode=1172188274400`, `usertot=1537`):

Prime factorisation gives multiple valid letter combinations. Brute-forcing all permutations against the `usertot` constraint (a position-weighted sum) yields several valid orderings ("daycha, adyhac, annach, ahnnac, hncaan, naanch"). The accepted username is **`annach`**.

**Password** (`passcode=1842055687879732800`, `passtot=393644`):

The prime factorisation of `passcode` maps to the character set `{a, d, g, g, l, o, o, r, v}`. Permuting these against the `passtot` constraint (a position-weighted sum of squared character codes) produces the password: **`volgograd`** — the Russian city formerly known as Stalingrad.

### Privilege Escalation

Logging in with `annach:volgograd` succeeds, but the page states that only users with admin privileges can access the key. The URL changes to a new parameter:

```
/secure.php?ss=FQEPBRAcExcLHxMABhYSEBMFXUZEWAQAFUQNUwERR18DVUFNXVRdRRFbBAdCRAtWBREWCVEFSkFWHREAER0=
```

No session cookie is set — the entire session state is carried in this base64-encoded `ss` parameter.

### Analysing the Encoding

Decoding the base64 gives 62 raw bytes. Using the known plaintext (`annach:volgograd:d9507edf0b2eb30b1292596e4ec10d7abbf0a959:user` — the token from the JS concatenated with a `:user` role suffix), XORing against the ciphertext reveals the key stream.

At every non-colon position, the XOR key byte cycles through the characters **`t, o, a, d, s`** (period 5), indexed by absolute position in the string. Colon characters are encoded separately and remain at fixed positions (6, 16, 57).

## Exploitation:

With the encoding scheme understood, constructing an admin token is straightforward: encrypt the modified plaintext `annach:volgograd:d9507edf0b2eb30b1292596e4ec10d7abbf0a959:admin` using the same XOR key, preserving the original colon bytes:

```python
import base64

data = base64.b64decode("FQEPBRAcExcLHxMABhYSEBMFXUZEWAQAFUQNUwERR18DVUFNXVRdRRFbBAdCRAtWBREWCVEFSkFWHREAER0=")
new_plain = "annach:volgograd:d9507edf0b2eb30b1292596e4ec10d7abbf0a959:admin"
key = "toads"

new_data = bytearray()
for i, ch in enumerate(new_plain):
    if ch == ':':
        new_data.append(data[i])  # preserve original colon encoding
    else:
        new_data.append(ord(ch) ^ ord(key[i % 5]))

print(base64.b64encode(bytes(new_data)).decode())
# FQEPBRAcExcLHxMABhYSEBMFXUZEWAQAFUQNUwERR18DVUFNXVRdRRFbBAdCRAtWBREWCVEFSkFWHQUXGQYP
```

Navigating to:

```
https://factxoryreset.web.baectf.com/secure.php?ss=FQEPBRAcExcLHxMABhYSEBMFXUZEWAQAFUQNUwERR18DVUFNXVRdRRFbBAdCRAtWBREWCVEFSkFWHQUXGQYP
```

Returns the key: **Remember that security by obscurity is never the answer**

## Key Takeaways & Remediation:

- Client-side authentication is no authentication at all. The "big number factoring" only requires basic number theory tooling to reverse — the credentials are fully recoverable from source.
- Session state and authorisation roles should never be carried in a client-controlled parameter. Like the OmNomNom challenge, the role (`user`/`admin`) is embedded in a value the client can freely modify.
- XOR with a short repeating key is not encryption. A known-plaintext attack trivially recovers the key stream, allowing arbitrary token forgery. Use authenticated encryption (e.g. AES-GCM) or signed tokens (e.g. HMAC-based JWTs) where the server holds a secret the client cannot access.
- Security by obscurity — hiding credentials behind "hard" maths or encoding schemes — collapses the moment an attacker can observe the mechanism, which in client-side code is always.