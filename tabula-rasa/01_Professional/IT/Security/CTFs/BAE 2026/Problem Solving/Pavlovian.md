---
date created: Sunday, February 15th 2026, 3:47:55 am
date modified: Sunday, February 15th 2026, 4:57:10 am
---

# Pavlovian
**Points:** 100pts
**Description:** Connect (using "nc" or PuTTY in raw mode) and follow the instructions. You'll probably need to write a script to solve it - see the Help section for more information.
**Source:** nc creds

# Method:
## Description & Investigation:

```Bash
pavlovian.baectf.com:443
Credentials: steeltalk

nc pavlovian.baectf.com 443
```

If you connect to the server, you are asked to repeat a message quickly, this message changes over time. The help section lists a script which we can modify an run in this case.

## Writing a Python Script for Connecting to Server:

First make sure we can setup our import correctly.
```Bash
python3 -m venv venv
source venv/bin/activate
pip install telnetlib
```

```Python
from telnetlib import Telnet
import time

HOST = 'pavlovian.baectf.com'
PORT = 443
PASSWORD = "steeltalk"

def solve_challenge(host, port, password):
    tn = Telnet(host, port)
    
    # 1. Handle Password Prompt
    print tn.read_until(": ")
    tn.write(password + "\n")
    
    # 2. Capture the randomized phrase
    time.sleep(0.5) # A short sleep ensures server has sent phrase
    phrase = tn.read_very_eager()
    print "Captured phrase: " + phrase
    
    # 3. Echo the phrase back exactly
    tn.write(phrase)
    
    # 4. Read the response (the flag)
    time.sleep(0.5)
    print tn.read_very_eager()
    
    tn.close()

if __name__ == "__main__":
    solve_challenge(HOST, PORT, PASSWORD)
```

You got it! The key is: 'Cat rang bell, I ate food.'



## Key Takeaways & Remediation:
