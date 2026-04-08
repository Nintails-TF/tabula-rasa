---
date created: Saturday, February 14th 2026, 3:10:42 pm
date modified: Saturday, February 14th 2026, 4:30:53 pm
---

# Friendly Android A

**Points:** 200
**Description:** Can you Quickly Realise where the key is?
**File:** You receive the `re005_6e13e4c182a386581f419230c775dc92.apk` (Java Archive data)

# Method:
## Description & Investigation:

Strings is too messy and long to read the `.apk` file. `file` returns the following:
```Bash
file re005_6e13e4c182a386581f419230c775dc92.apk 
re005_6e13e4c182a386581f419230c775dc92.apk: Java archive data (JAR)
```

So we need a tool that we can analyse the `.apk` with. I've gone with [Jadx](https://github.com/skylot/jadx?tab=readme-ov-file) for this reason.

## Installing and Using Jadx:

First we can install Jadx like so:
```Bash
sudo apt update
sudo apt install jadx
```

Then we can run `jadx-gui`, like so:
```bash
jadx-gui
```

## Looking Around:

We can see that within `res/resources/drawable`, we have a QR-code which contains the credentials. When we scan it, we get the phrase:

**I prefer code 128**
## Key Takeaways & Remediation:

- This proves my previous theory, that smartphones would be used again. Of course I could of used an online QR-code scanner or another tool.
	- Shows that smartphones are likely going to be/are another tool in the box for security professionals now or in the close future.
- Proper obfuscation should be done through tools like [ProGuard](https://github.com/Guardsquare/proguard) or [R8](https://developer.android.com/topic/performance/app-optimization/enable-app-optimization). Which would make reverse engineering harder and more laborious, but not prevent it.
- The android keystore system can work effectively if you need to store data locally, as this meaning that the key material is stored in a Trusted Execution Environment (TEE) or Secure Element (SE).
	- e.g. configure a key so that you can only use it after biometric authentication.
- Server-sided storage though is the golden solution, don't include sensitive information on an APK, but fetch data after the user has been authenticated over HTTPS.

