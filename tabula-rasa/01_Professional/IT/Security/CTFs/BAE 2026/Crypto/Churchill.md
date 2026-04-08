---
date created: Sunday, February 15th 2026, 3:13:32 am
date modified: Sunday, February 15th 2026, 3:26:10 am
---

# Churchill:

**Points:** 200
**Description:** The key is the key, lower case. It'll kind of make sense.
**Source:** File

# Method:

## Description & Investigation:

We are given the following ciphertext:
```plaintext
Zu sktww cx xf vx vku ufq, zu sktww ibckv bf Iptfeu, zu sktww ibckv xf vku suts tfq xeutfs, zu sktww ibckv zbvk cpxzbfc exfibqufeu tfq cpxzbfc svpufcvk bf vku tbp, zu sktww quiufq xlp bswtfq, zktvuaup vku exsv ntd hu, zu sktww ibckv xf vku hutekus, zu sktww ibckv xf vku wtfqbfc cpxlfqs, zu sktww ibckv bf vku ibuwqs tfq bf vku svpuuvs, zu sktww ibckv bf vku kbwws; zu sktww fuaup slppufqup, tfq uauf bi, zkbek B qx fxv ixp t nxnufv huwbuau, vkbs bswtfq xp t wtpcu jtpv xi bv zupu slhrlctvuq tfq svtpabfc, vkuf xlp unjbpu hudxfq vku suts, tpnuq tfq cltpquq hd vku Hpbvbsk iwuuv, zxlwq etppd xf vku svplccwu, lfvbw, bf Cxq's cxxq vbnu, vku fuz zxpwq, zbvk tww bvs jxzup tfq nbckv, svujs ixpvk vx vku puselu tfq vku wbhuptvbxf xi vku xwq.
```

The challenge is named "Churchill" and the description says "the key is the key, lower case. It'll kind of make sense.", so the cipher key relates to the word "key" somehow.

Initial observations through frequency analysis:

- `zu` appears frequently — likely maps to a common two-letter word like "we".
- `sktww` repeats — the double `w` at the end suggests a word like "shall".
- `vku` appears throughout — a three-letter word starting with `v`, likely "the".
- `tfq` recurs often — probably "and".
- The single capital `B` in the text likely maps to `I`.

Given the challenge name and these patterns, the plaintext is almost certainly Churchill's famous **"We shall fight on the beaches"** speech (June 4, 1940). This gives us a strong crib to work with.
## Extraction & Discovery:

Since each letter consistently maps to the same replacement (e.g., `v` is always `t`, `k` is always `h`), this is a **monoalphabetic substitution cipher**. However, the shifts aren't consistent across letters, ruling out a simple Caesar cipher.

By aligning the known plaintext against the ciphertext, we can extract the full substitution alphabet:

```
Plain:  a b c d e f g h i j k l m n o p q r s t u v w x y z
Cipher: t h e q u i c k b r ? w n f x j ? p s v l a z ? d ?
```

Which spells out: `thequickbrownfoxjumpsoverthelazydog` — deduplicated to 26 unique letters: `thequickbrownfxjmpsvlazydg`.

The key is **"the quick brown fox jumps over the lazy dog"** — the classic pangram used to test every **key** on a keyboard. The hint "the key is the key" is a double meaning: the cipher key is literally about keyboard keys.

We can confirm by decrypting with the following script:

```python
#!/usr/bin/env python3

import string

# Build cipher alphabet from the pangram (deduplicated)
phrase = "thequickbrownfoxjumpsoverthelazydog"
seen = set()
cipher_alpha = []
for c in phrase:
    if c not in seen and c.isalpha():
        seen.add(c)
        cipher_alpha.append(c)
cipher_alpha = ''.join(cipher_alpha)

# Build decryption mapping: cipher letter -> plain letter
plain_alpha = string.ascii_lowercase
c2p = {}
for i, c in enumerate(cipher_alpha):
    c2p[c] = plain_alpha[i]
    c2p[c.upper()] = plain_alpha[i].upper()

ciphertext = "Zu sktww cx xf vx vku ufq, zu sktww ibckv bf Iptfeu, zu sktww ibckv xf vku suts tfq xeutfs, zu sktww ibckv zbvk cpxzbfc exfibqufeu tfq cpxzbfc svpufcvk bf vku tbp, zu sktww quiufq xlp bswtfq, zktvuaup vku exsv ntd hu, zu sktww ibckv xf vku hutekus, zu sktww ibckv xf vku wtfqbfc cpxlfqs, zu sktww ibckv bf vku ibuwqs tfq bf vku svpuuvs, zu sktww ibckv bf vku kbwws; zu sktww fuaup slppufqup, tfq uauf bi, zkbek B qx fxv ixp t nxnufv huwbuau, vkbs bswtfq xp t wtpcu jtpv xi bv zupu slhrlctvuq tfq svtpabfc, vkuf xlp unjbpu hudxfq vku suts, tpnuq tfq cltpquq hd vku Hpbvbsk iwuuv, zxlwq etppd xf vku svplccwu, lfvbw, bf Cxq's cxxq vbnu, vku fuz zxpwq, zbvk tww bvs jxzup tfq nbckv, svujs ixpvk vx vku puselu tfq vku wbhuptvbxf xi vku xwq."

result = []
for ch in ciphertext:
    if ch in c2p:
        result.append(c2p[ch])
    else:
        result.append(ch)

print(''.join(result))
```

```
We shall go on to the end, we shall fight in France, we shall fight on the seas and oceans, we shall fight with growing confidence and growing strength in the air, we shall defend our island, whatever the cost may be, we shall fight on the beaches, we shall fight on the landing grounds, we shall fight in the fields and in the streets, we shall fight in the hills; we shall never surrender, and even if, which I do not for a moment believe, this island or a large part of it were subjugated and starving, then our empire beyond the seas, armed and guarded by the British fleet, would carry on the struggle, until, in God's good time, the new world, with all its power and might, steps forth to the rescue and the liberation of the old.
```

## Key Takeaways & Remediation:
- Monoalphabetic substitution ciphers are vulnerable to **frequency analysis** — repeating patterns like `zu`, `vku`, and `sktww` immediately expose common English words.
- A **known-plaintext crib** (recognising the Churchill speech from context and repetition patterns) makes breaking the cipher trivial — the challenge name itself was a massive hint.
- The hint structure used a clever double meaning: "the key is the key" refers both to the cipher key and to keyboard keys (the pangram). Always think laterally about challenge descriptions.
- Pangram-based substitution alphabets are a well-known cipher construction method — worth keeping in mind for future CTF challenges.