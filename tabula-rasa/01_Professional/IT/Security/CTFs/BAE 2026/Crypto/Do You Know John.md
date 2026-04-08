---
date created: Sunday, February 15th 2026, 3:33:37 am
date modified: Sunday, February 15th 2026, 4:08:04 am
---

# Do You Know John

**Points:** 400 
**Description:** N/A 
**Source:** `cry004_72361cb48c8ee6252eef92ad6d0b9f10.zip` containing `key.zip`, `intro.txt`, `passwd_file`

# Method:

## Description & Investigation:

Extracting the archive gives us three files. The `intro.txt` provides the challenge framing:
```plaintext
The password for the next set of challenges is contained within the included encrypted ZIP file.
The password for the ZIP file is in the following format:
[Username][password]
eg
Emmanuelpassw
Where Emmanuel is the username and the password is 'passw'
HINT:
The password file is from an antiquated Unix system. The DES hashed passwords are ALL 5 characters long and contain ONLY lower case letters. The password file is in standard Unix 'passwd' format.
```

The `passwd_file` contains four users with traditional Unix DES-crypt hashes:
```
Zoraida:ij1ci3JJDjm/U:6160:6160::/home/Zoraida:/bin/sh
Zula:7ThYKnAukL9ro:6161:6161::/home/Zula:/bin/sh
Zulema:Nl/V5/a6gtTns:6162:6162::/home/Zulema:/bin/sh
Zulma:Q7jaM0fbWrIB.:6163:6163::/home/Zulma:/bin/sh
```

These are old-style Unix passwd entries where the hash sits directly in the second field — no shadow file separation. The challenge name "Do You Know John" is a clear nod to **John the Ripper**, the classic password cracking tool.

## Extraction & Discovery:

### Step 1: Crack the DES Hashes:

Given the hint that all passwords are exactly 5 lowercase letters, we can use John the Ripper with a mask attack to constrain the search space:

```bash
john --format=descrypt --mask='?l?l?l?l?l' passwd_file
```

This limits the keyspace to `26^5 = 11,881,376` combinations — trivial for DES. Time go make some coffee.
### Step 2: Build the ZIP Wordlist:

Per the instructions, the ZIP password follows the format `[Username][password]`. With ~6,500 cracked accounts, we generate all combinations automatically:

```bash
john --show passwd_file | grep -v "^$" | awk -F: '{print $1$2}' > wordlist.txt
```

This produces a wordlist of ~6,160 entries like `Zoraidaatstus`, `Lovettatstus`, `Zulastqba`, etc.
### Step 3: Crack the ZIP:

First, extract the ZIP hash using `zip2john`:

```bash
zip2john key.zip > zip.hash
```

Then crack it against our wordlist:
```bash
john --wordlist=wordlist.txt zip.hash

Lovettatstus     (key.zip/key.txt)
```

The winning combination was **Lovetta** + **atstus**.
### Step 4: Extract the Key:

``` Bash
unzip key.zip
cat key.txt
```
```Plaintext
I promise not to crack passwords in real life, but I have learned why low complexity passwords are bad!
```

## Key Takeaways & Remediation:

- **DES-crypt is obsolete** — with a maximum effective key length of 8 characters and no salting uniqueness, it's trivially brute-forced on modern hardware. Even with 6,163 accounts, the entire 5-character lowercase keyspace was cracked without difficulty.
- **Old-style Unix passwd files** stored hashes in a world-readable file — the move to `/etc/shadow` with restricted permissions was a critical security improvement.
- **Password composition rules matter** — 5 lowercase letters gives only ~11.8 million combinations. Even modest complexity requirements (mixed case, digits, symbols) exponentially increase the keyspace.
- **John the Ripper's pot file** (`~/.john/john.pot`) persists cracked results across sessions, so progress isn't lost if the tool is interrupted — useful to know for longer cracking jobs.