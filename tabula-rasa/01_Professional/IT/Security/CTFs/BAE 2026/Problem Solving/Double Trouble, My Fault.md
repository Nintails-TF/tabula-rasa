---
date created: Sunday, February 15th 2026, 3:49:48 am
date modified: Sunday, February 15th 2026, 5:08:06 am
---

# Double Trouble, My Fault
**Points:** 150pts
**Description:** Decode the transmission and get the key
**Source:** mp3 file

# Method

## Description & Investigation

We are given a 13-second audio file called `prb013_8ff9595f13cc918cb48a220ba6992cc1.mp3`. Examining the file metadata reveals the title **"Two by Two"** dated 1980, encoded as MPEG Layer III at 11.025 kHz mono — an unusually low sample rate that immediately suggests the audio content is functional rather than musical.

Listening to the file, it's clearly not speech or music — it consists of a rapid sequence of short, distinct tones. The low sample rate and synthetic quality point towards some form of data-over-audio encoding.

## Extraction & Discovery

### Identifying the Encoding: DTMF

Generating a spectrogram reveals the tell-tale signature of **DTMF (Dual-Tone Multi-Frequency)** signalling, the same system used by touch-tone telephones. Each tone burst contains exactly two simultaneous frequencies: one from a low group (697, 770, 852, 941 Hz) and one from a high group (1209, 1336, 1477, 1633 Hz). The intersection of these two frequencies maps to a specific digit on the phone keypad.

Using frequency analysis (FFT over sliding windows), each tone burst was decoded to its corresponding keypad digit, yielding the following 64-digit sequence:

```
8772658439833284726584326776736775737871327978327789328072797869
```

### Decoding the Digits: "Two by Two"

The metadata title **"Two by Two"** serves as the critical hint. Taking the digits in **pairs** and interpreting each pair as a **decimal ASCII character code**:

|Pair|ASCII|Char|
|---|---|---|
|87|87|W|
|72|72|H|
|65|65|A|
|84|84|T|
|39|39|'|
|83|83|S|
|32|32|_(space)_|
|84|84|T|
|72|72|H|
|65|65|A|
|84|84|T|
|...|...|...|

This decodes to the key:
```
WHAT'S THAT CLICKING ON MY PHONE
```

### Full Decoding Pipeline
```
Audio (mp3) → DTMF frequency detection → Digit sequence → Pair as ASCII → Plaintext
```

## Key Takeaways & Remediation
- **Metadata matters.** The file title "Two by Two" was the crucial hint for the final decoding step. Always inspect ID3 tags and other metadata — challenge authors frequently hide clues there.
- **DTMF is a common audio-steganography vector in CTFs.** Any audio with short, clean tone bursts at telephone frequencies (roughly 697–1633 Hz) should immediately suggest DTMF. Tools like `multimon-ng` can automate detection, but understanding the underlying frequency pairs helps when automated tools fail.
- **Layered encoding is the norm.** This challenge required two stages of decoding: first recognising the audio as DTMF, then interpreting the resulting digits as paired ASCII values rather than raw phone numbers. When a first-pass decode produces something that doesn't look like a flag, consider that there's another layer.
- **The real-world parallel is wiretapping.** The decoded message — _"WHAT'S THAT CLICKING ON MY PHONE"_ — references the classic sign of an analogue phone tap. Historically, DTMF tones transmitted in-band were vulnerable to interception, which is one reason modern telephony moved to out-of-band signalling.
