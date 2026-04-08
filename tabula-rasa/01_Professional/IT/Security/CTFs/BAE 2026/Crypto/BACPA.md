---
date created: Sunday, February 15th 2026, 4:08:05 am
date modified: Sunday, February 15th 2026, 4:29:29 am
---

# BACPA

**Points:** 600pts
**Description:** This program is running on the specified port
**Source:** `skillz.baectf.com:44433` + source code for the program.

# Method:

## Description & Investigation:

Connecting to the service, it immediately sends 16 bytes (an IV), then enters a loop: you send 4 bytes indicating a plaintext length, then the plaintext itself. The server **appends a secret** (`CHALLENGE_KEY`) to your input, pads with PKCS7, encrypts with AES-CBC, and returns the ciphertext. The IV for each subsequent encryption is the last ciphertext block from the previous one.

Key observations from the source code:
```Python
# Character set: uppercase letters and space.
BLOCK_SIZE = 16 

# Append the secret
data += CHALLENGE_KEY

# Encrypt it
ciphertext = encrypt(data, iv)

# The IV for the next block is the ciphertext for this block.
iv = ciphertext[-16:]
```

The source code tells us:

1. The character set is **uppercase letters and spaces only.** (27 candidates)
2. We're using a block-size of 16-bytes, each block is encrypted independently.

This is a textbook **byte-at-a-time chosen-plaintext attack** — the same family as the classic ECB (Electronic Codebook) byte-at-a-time, but adapted for CBC (Cipher Block Chaining) mode.

## Extraction & Discovery:

### The Core Idea:

In AES-CBC, each plaintext block is XORed with the previous ciphertext block (or the IV for block 0) before encryption:

```
C_i = AES(P_i ⊕ C_{i-1})
```

Since the server appends the secret to our controlled input, we can choose the padding length so that exactly **one unknown byte** of the secret lands at the end of a ciphertext block boundary. We then brute-force that byte by comparing ciphertext blocks.

For secret byte `n` (0-indexed):
- **Padding length** = `15 - (n % 16)` — pushes the unknown byte to position 15 of the target block.
- **Target block** = `n // 16` — which ciphertext block contains the unknown byte.

### Compensating for CBC Chaining:

The complication over ECB is that the IV changes between encrypt calls (set to the last ciphertext block). So even identical plaintext produces different ciphertext.

The fix: XOR-adjust block 0 of our brute-force input to cancel out the IV difference. If the reference encryption used `IV_ref` and our current IV is `IV_current`, we transform our guess:

```
adjusted_block0 = guess_block0 ⊕ IV_ref ⊕ IV_current
```

This makes the AES input identical when the candidate byte matches, producing a matching ciphertext block. For target blocks beyond block 0, this adjustment propagates correctly through the CBC chain — if block 0's ciphertext matches the reference, then block 1's chaining value also matches, and so on.

### Step 1: The Attack Loop:

For each byte position, we open a fresh connection and:
1. Send `pad_len` bytes of `'A'` to get a **reference ciphertext** — noting the target block.
2. For each candidate byte `b` in `[A-Z, space]`:
    - Construct the full guess: `'A' * pad_len + known_secret + b`
    - XOR-adjust block 0 for the IV difference
    - Send it and compare the target ciphertext block against the reference
3. When a match is found, that's the next byte of the secret.

```python
for b in CHARSET:
    guess = padding + known + bytes([b])
    block0 = guess[:16]
    block0_adj = xor_bytes(block0, xor_bytes(iv_ref, current_iv))
    adjusted = block0_adj + guess[16:]

    ct = send_encrypt(s, adjusted)
    current_iv = ct[-16:]

    if ct[target_block * 16:(target_block + 1) * 16] == ref_block:
        known += bytes([b])
        break
```

### Step 2: Run It:

```bash
python3 exploit.py
```

```
[*] Target: skillz.baectf.com:44433
[*] Charset: 27 candidates (A-Z + space)
[*] Attack: byte-at-a-time CBC chosen plaintext
============================================================
[+] Byte  0: 'N' | Secret: "N"
[+] Byte  1: 'O' | Secret: "NO"
[+] Byte  2: 'B' | Secret: "NOB"
[+] Byte  3: 'O' | Secret: "NOBO"
...
[+] Byte 47: 'E' | Secret: "NOBODY WOULD DO SUCH A BEASTLY THING IN REAL LIFE"
[*] No match at byte 48 — likely end of secret.
============================================================
[+] CHALLENGE_KEY = "NOBODY WOULD DO SUCH A BEASTLY THING IN REAL LIFE"
```

## Key Takeaways & Remediation:

- **Never append secrets to user-controlled plaintext before encrypting** — this is the fundamental flaw. If the attacker controls the prefix and can observe the ciphertext, they can recover the secret byte-by-byte regardless of the encryption algorithm's strength. AES could be unbreakable and it wouldn't matter; the protocol design is what's broken.
- **CBC doesn't save you from ECB-style attacks here** — the IV chaining adds a step (XOR compensation), but doesn't prevent the attack. The attacker just needs to account for the known IV difference, which is trivial since the IVs are sent in the clear.
- **The keyspace is tiny** — 27 candidates per byte means at most `27 × secret_length` encrypt calls. For a 49-character secret, that's under 1,400 requests. Even with network latency, this completes in well under a minute.
- **Encrypt-then-MAC and authenticated encryption (AES-GCM)** would prevent ciphertext analysis, but the real fix is architectural: don't construct plaintexts by concatenating attacker-controlled data with secrets. Use HMACs or separate key derivation if you need to bind user data to a secret.