---
date created: Wednesday, November 19th 2025, 2:51:39 pm
date modified: Wednesday, November 19th 2025, 3:32:31 pm
---

# BabyEncryprion:

**Challenge Description:**
```Plaintext
You are after an organised crime group which is responsible for the illegal weapon market in your country. As a secret agent, you have infiltrated the group enough to be included in meetings with clients. During the last negotiation, you found one of the confidential messages for the customer. It contains crucial information about the delivery. Do you think you can decrypt it?
```

# Initial Overview:

You have two files: `chall.py` and `msg.enc`. `chall.py` is the method used to encrypt the message text. 

The code is as followed:
```python
import string
from secret import MSG

def encryption(msg):
    ct = []
    for char in msg:
        ct.append((123 * char + 18) % 256)
    return bytes(ct)

ct = encryption(MSG)
f = open('./msg.enc','w')
f.write(ct.hex())
f.close()
```

## Code Review:

1. The encryption function takes in a string and loops for each character in the message performing an append to obfuscate the characters.
	1. Is this some kind of offset? in which each character is being mangled using the offset values?
2. This data is returned an array which is converted into bytes.
3. Before being written to file, the text is converted into hexadecimal using the `.hex()` function.

So to reverse we would need to do the following:
1. Dehex the message data.
2. Reverse the bytes operation
3. Figure out how to remove the offset value.

`msg.enc` is the encrypted message text, it is as followed:
```Bash                           
cat msg.enc                             
6e0a9372ec49a3f6930ed8723f9df6f6720ed8d89dc4937222ec7214d89d1e0e352ce0aa6ec82bf622227bb70e7fb7352249b7d893c493d8539dec8fb7935d490e7f9d22ec89b7a322ec8fd80e7f8921
```

## Reversing Decryption:

We can reverse the encryption by performing the opposite of the mathematical operations.

This involves:
1. Subtracting 18
	1. Easy!
2. Divide by 123
	1. Since we'd end up dividing by 0 this wouldn't work, so we need to **find the inverse of 123**.
	2. This can be done in a few different ways.
		1. Brute-force, check the inverse of each value
		2. Python built in function
		3. Implementation of EEA (Extended Euclidian Algorithm)
	3. e.g. `123 × 179 = 22017` and `2017 % 256 = 1` meaning that multiplying by 179 undoes multiplying 123 with modulo 256, which enables us to decrypt.

The real challenge would be figuring out how to decrypt with larger values that you couldn't brute force. In this case you'd use **Extended Euclidian Algorithm.**

| Method                           | When to Use                        | Complexity                       |
| -------------------------------- | ---------------------------------- | -------------------------------- |
| **Brute Force**                  | Numbers < 10,000                   | O(n) - tries every possibility   |
| **`pow(a, -1, m)`**              | Python 3.8+, any size              | O(log m) - built-in optimization |
| **Extended Euclidean Algorithm** | Any programming language, any size | O(log m) - efficient math        |
For a harder decryption challenge you'd want to not use brute force.


This would look like:
```Python
ct_hex = "6e0a9372ec49a3f6930ed8723f9df6f6720ed8d89dc4937222ec7214d89d1e0e352ce0aa6ec82bf622227bb70e7fb7352249b7d893c493d8539dec8fb7935d490e7f9d22ec89b7a322ec8fd80e7f8921"

# Convert hex to bytes
ct_bytes = bytes.fromhex(ct_hex)

# Decrypt: char = ((byte - 18) * 179) % 256
# (179 is the modular inverse of 123 mod 256)
msg = ""  
for byte in ct_bytes:
    char = ((byte - 18) * 179) % 256
    msg += chr(char)

print(msg)
```

We can use in built python functions to convert to reverse the encryption of the bytes and hex.
## Flag:
```
Th3 nucl34r w1ll 4rr1v3 0n fr1d4y.
HTB{l00k_47_y0u_r3v3rs1ng_3qu4710n5_c0ngr475}
```

The flag states that you'd need to understand the Extended Euclidean algo to understand what is going on, asking an LLM or internet works just fine here.

