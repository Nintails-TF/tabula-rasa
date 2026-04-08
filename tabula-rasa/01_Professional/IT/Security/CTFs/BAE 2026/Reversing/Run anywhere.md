---
date created: Saturday, February 14th 2026, 4:33:38 pm
date modified: Saturday, February 14th 2026, 6:16:52 pm
---

# Run Anywhere

**Points:** 300
**Description:**
**File:** A `re004_b0a533dab0373cc486ca1fb3a7351fc9.class` (Compiled Java Class, Java 1.7.)
# Method:
## Description & Investigation:

Using `strings`:
```Bash
strings re004_b0a533dab0373cc486ca1fb3a7351fc9.class

...SNIP...
chal.java # The original file name
javax/crypto/spec/SecretKeySpec # There is a secret key
!javax/crypto/spec/IvParameterSpec # and starting IV
DES/CBC/PKCS5Padding # The class is protecting using these algorithms (JCA)
...SNIP...

```

The rest of the strings output can lead us to figuring out some more details:

- `encrypted` refers to the encrypted variable of a byte array (our phrase!)
	- This theory is further supported by the: `()[B` line which indicates a byte array is being used, similarly to: [[It's the code breaker]].

To progress further, we need to move towards decompiling it. We can open it up in [Jadx](https://github.com/skylot/jadx?tab=readme-ov-file)again.
## Decomposition of the `.class` File:

Within Jadx, we can navigate to the source code area and look at `decryptData`:

```Java
package defpackage;  
  
import java.security.InvalidAlgorithmParameterException;  
import java.security.InvalidKeyException;  
import java.security.NoSuchAlgorithmException;  
import javax.crypto.Cipher;  
import javax.crypto.NoSuchPaddingException;  
import javax.crypto.ShortBufferException;  
import javax.crypto.spec.IvParameterSpec;  
import javax.crypto.spec.SecretKeySpec;  
  
/* compiled from: chal.java */  
/* loaded from: re004_b0a533dab0373cc486ca1fb3a7351fc9.class */  
class decryptData {  
    private byte[] encrypted = {124, 72, 53, 85, 34, -117, 63, 119, -62, -62, -62, -39, 73, 117, -72, -46, 59, -120, 64, -105, -87, 18, 75, -97, -58, -2, 11, 84, -106, 61, -56, -114, -116, 19, -64, -28, -76, -47, -46, -67, -28, 99, 118, -120, -89, 14, -65, 80};  
    private boolean printKey = false;  
  
    public byte[] decrypt() throws NoSuchPaddingException, NoSuchAlgorithmException, InvalidKeyException, InvalidAlgorithmParameterException, ShortBufferException {  
        byte[] bArr = null;  
        byte[] bArr2 = {11, -83, -16, 13, 11, -83, -16, 13};  
        byte[] bArr3 = new byte[8];  
        for (int i = 0; i < bArr3.length; i++) {  
            bArr3[i] = -51;  
        }  
        SecretKeySpec secretKeySpec = new SecretKeySpec(bArr2, "DES");  
        IvParameterSpec ivParameterSpec = new IvParameterSpec(bArr3);  
        try {  
            Cipher cipher = Cipher.getInstance("DES/CBC/PKCS5Padding");  
            cipher.init(1, secretKeySpec, ivParameterSpec);  
            cipher.init(2, secretKeySpec, ivParameterSpec);  
            bArr = new byte[cipher.getOutputSize(this.encrypted.length)];  
            int iUpdate = cipher.update(this.encrypted, 0, this.encrypted.length, bArr, 0);  
            int iDoFinal = iUpdate + cipher.doFinal(bArr, iUpdate);  
        } catch (Exception e) {  
        }  
        return bArr;  
    }  
  
    public void go() {  
        if (this.printKey) {  
            System.out.println(new String(decrypt()));  
        } else {  
            System.out.println("Sorry, can't help you!");  
        }  
    }  
  
    public static void main(String[] strArr) {  
        System.out.println("Here we go...");  
        new nested().go();  
    }  
}
```

So, there are many ways you could solve this problem:
1. Easiest method is to modify the code and recompile it
	1. Flip print key from false -> true.
	2. You could use CyberChef to decrypt it visually.
	3. Write it in another language.

## My Initial Method:

We can build the python file to decrypt this:
```Python
from Crypto.Cipher import DES

# Convert Java signed bytes to Python unsigned bytes
ciphertext = bytes([124, 72, 53, 85, 34, 139, 63, 119, 194, 194, 194, 217, 73, 117, 184, 210, 59, 136, 64, 151, 169, 18, 75, 159, 198, 254, 11, 84, 150, 61, 200, 142, 140, 19, 192, 228, 180, 209, 210, 189, 228, 99, 118, 136, 167, 14, 191, 80])
key = bytes([11, 173, 240, 13, 11, 173, 240, 13])
iv = bytes([205] * 8) # -51 in Java is 205 in unsigned

cipher = DES.new(key, DES.MODE_CBC, iv)
plaintext = cipher.decrypt(ciphertext)

print(plaintext.decode('utf-8'))
```

To run, we need to make a venv:
```Bash
python3 -m venv venv # Make a virtual environemt
source venv/bin/activate # Activate it
pip install pycryptodome # Since we need the Crypto library
python run-anywhere-decrypt.py # Run our script to decrypt.
```

Our key is: **I am serious...and don't call me Shirley.**
# Alternative Solution:

Make sure we've got the dependencies to compile code:
```Bash
sudo apt install default-jdk # Need the Java dev kit to compile
```

First we can decompile using jadx:
```Bash
jadx -d /home/kali/Downloads/run-anywhere /home/kali/Downloads/run-anywhere/re004_b0a533dab0373cc486ca1fb3a7351fc9.class
```

We get the file: `decryptData.class`. Then we can modify the code through `nano`:
```Java
private boolean printKey = true; // Line 16 private boolean printKey = false;
new decryptData().go(); // Line 49 new nested().go();
```

Then update both `main()` and `go()` to throw exceptions:
```Java
public void go() throws Exception
public static void main(String[] strArr) throws Exception
```


Then we can run it:
```Bash
java decryptData.java 
Here we go...
"I am serious...and don't call me Shirley."
```


## Key Takeaways & Remediation:

- Decompiling code rarely compiles cleanly, you've got to do lots of debugging.
- Many solutions exist for a problem
