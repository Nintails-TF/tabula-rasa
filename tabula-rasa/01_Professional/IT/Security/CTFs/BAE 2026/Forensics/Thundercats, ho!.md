---
date created: Saturday, February 14th 2026, 11:44:22 am
date modified: Saturday, February 14th 2026, 1:03:11 pm
---

# Thundercats, Ho!

**Points:** 150pts
**Description:** We found this data on a command-and-control server, we think they captured someone's passphrase. What is it?
**File:** A zipped file (`for004_9b664f7b938bfae8e4bdfe9922b51e41.zip`) that contains 6 images (`1.png, 2.png, etc`).
# Method:
## Description & Investigation:

The photos look like a phone lock screen, that shows a trail of a finger gesture. It looks like the android pattern lock, I've seen some of my friends have. But since the challenge is looking for a phrase or password, it should relate to some sort of text. Perhaps a keyboard?

Not sure what Thundercats have to do with this challenge, yet. But probably some sort of phrase from the TV show as the password.

## Analysis of Images:

First I'm going to consider taps on the keyboard and try get the phrases from swipe typing on gboard:

- `1.png`: `i`
- `2.png`: `could`
- `3.png`: `do`
- `4.png`: `with`
- `5.png`: `a`
- `6.png`: `stylus`

That's it, the phrase is "I could do with a stylus"

## Key Takeaways & Remediation:

- Sometimes the title of a challenge can be a red herring.
- As the previous challenge ("Listen carefully"), had a hint that relates to shazam. There will probably be more challenges that require the usage of a smartphone.
