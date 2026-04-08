---
date created: Sunday, February 15th 2026, 5:02:35 am
date modified: Sunday, February 15th 2026, 5:34:04 am
---

# Adding

**Points:** 250pts
**Description:** Decode the transmission and get the key by solving layered math problems under a time limit.
**Source:** `pavlovian.baectf.com:443`

# Method

## Description & Investigation

The challenge involves connecting to a remote server that requires a password (`hypeavenue`) to begin. Once authenticated, the server presents a multi-stage math challenge with a strict **10-second time limit** from the moment of connection.

The prompt explicitly states that the response must be returned as a string or binary, depending on the stage, followed by a new line. Given the short window and the switch from text to raw binary data, manual calculation is impossible, requiring a robust automation script.

## Extraction & Discovery

### Stage 1: ASCII Addition

The first stage provides four large integers as ASCII strings, separated by spaces.

```Plaintext
Here are the numbers:
987611824 93928090 496184900 322082431 
```

The script uses regular expressions (`re.findall(r'\d+', ...)`) to isolate these numbers from the surrounding text, sums them, and returns the result as a plaintext string. This stage tests basic socket automation and string parsing.

### Stage 2: Binary Little-Endian

After a successful Stage 1 response, the server immediately pivots to a binary challenge. The instructions specify:
- **Format:** 4 random numbers.
- **Encoding:** 4 bytes long, unsigned, Little-Endian binary.
- **Return Format:** The sum must be sent back in the same binary format.

In this stage, data is transmitted as raw bytes. For example, the number `1` is sent as the byte sequence `\x01\x00\x00\x00`.

Using Python’s `struct` module, the 16-byte payload (4 integers × 4 bytes) is unpacked using the format string `<IIII`. The sum is then calculated and masked with `& 0xFFFFFFFF` to simulate 32-bit integer overflow, ensuring the result fits back into the 4-byte format requested by the server.

### Full Automation Pipeline

``` Plaintext
Socket Connection → Password Auth → Regex Parse (ASCII) → Sum & Send (String) → Buffer 16 Bytes → Struct Unpack (Binary) → Sum & Mask → Struct Pack → Send (Binary) → Flag
```

## Key Takeaways & Remediation

- **Protocol Reliability:** Raw `socket` communication is more reliable for binary data than `telnetlib`, as Telnet may misinterpret certain binary bytes as control commands.
- **Handling Fragmentation:** Network packets often arrive in chunks. The script implements a loop to ensure all 16 bytes of binary data are collected (`while len(raw_data) < 16`) before processing.
- **Integer Overflow:** In 32-bit unsigned systems, sums exceeding $2^{32}-1$ must wrap around. Masking the result ensures the binary "pack" operation produces a valid 4-byte response.
    

---

## Final Script (Python 2.7)

```Python
import socket
import re
import struct
import time

HOST = 'pavlovian.baectf.com'
PORT = 443
PASSWORD = "hypeavenue"

def solve_challenge():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(5.0)
    
    try:
        s.connect((HOST, PORT))
        
        # 1. Handle Password Prompt
        print s.recv(1024)
        s.sendall(PASSWORD + "\n")
        
        # --- STAGE 1: ASCII ---
        print "--- Starting Stage 1 (ASCII) ---"
        buffer = ""
        while "numbers:" not in buffer:
            buffer += s.recv(1024)
        
        while len(re.findall(r'\d+', buffer.split("numbers:")[-1])) < 4:
            buffer += s.recv(1024)
        
        ascii_numbers = re.findall(r'\d+', buffer.split("numbers:")[-1])[:4]
        ascii_sum = sum(int(n) for n in ascii_numbers)
        print "Found ASCII Numbers: " + str(ascii_numbers)
        s.sendall(str(ascii_sum) + "\n")

        # --- STAGE 2: BINARY ---
        print "\n--- Starting Stage 2 (Binary) ---"
        binary_buffer = ""
        while "numbers:" not in binary_buffer:
            binary_buffer += s.recv(1024)

        data_start_pos = binary_buffer.find("numbers:") + len("numbers:")
        raw_data = binary_buffer[data_start_pos:].lstrip('\n\r ')

        while len(raw_data) < 16:
            raw_data += s.recv(1)
        
        binary_payload = raw_data[:16]
        print "Received Binary (Hex): " + binary_payload.encode('hex')

        bin_numbers = struct.unpack('<IIII', binary_payload)
        print "Found Binary Numbers: " + str(bin_numbers)
        
        bin_sum = sum(bin_numbers) & 0xFFFFFFFF
        print "Sending Binary Sum: " + str(bin_sum)

        s.sendall(struct.pack('<I', bin_sum))

        # --- GET THE FLAG ---
        time.sleep(1)
        print "\nFinal Response:"
        print s.recv(4096)

    except Exception as e:
        print "\n[!] Error: " + str(e)
    finally:
        s.close()

if __name__ == "__main__":
    solve_challenge()
```