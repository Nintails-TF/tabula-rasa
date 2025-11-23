---
date created: Wednesday, November 19th 2025, 3:39:51 pm
date modified: Wednesday, November 19th 2025, 4:26:16 pm
---

# PhishNet

**Challenge Description:**
*An accounting team receives an urgent payment request from a known vendor. The email appears legitimate but contains a suspicious link and a .zip attachment hiding malware. Your task is to analyse the email headers, and uncover the attacker's scheme.*

# Challenge Deliverables:

We have an email file, `email.eml`, in which we need to find the following details

- IP address of the sender
	- `45.67.89.10`
- What mail server relayed this email before reaching the victim
	- `mail.business-finance.com (IP address: 203.0.113.25)`
- Sender's email address
	- `finance@business-finance.com`
- Reply-To email address
	- `support@business-finance.com`
- Sender Policy Framework (SPF) result of the email
	- `Pass (protection.outlook.com: domain of business-finance.com designates 45.67.89.10 as permitted sender)`
- What domain is used for phishing?
	- `secure.business-finance.com`
- What is the fake company name used
	- `Business Finance Ltd.`
- What is the malicious attachment name?
	- `Invoice_2025_Payment.zip`
- What is the SHA-256 hash of the attachment
	- 8379c41239e9af845b2ab6c27a7509ae8804d7d73e455c800a551b22ba25bb4a
- What is the filename contained within the zip?
	- `invoice_document.pdf.bat`
- Which MITRE ATT&CK techniques are associated with this attack.
	- `T1566.001` - Phishing: Spearphishing Attachment

## Grabbing Initial Email Details.

The first things we can do is to look at the plaintext within the email.

```bash
less email.eml
```

This reveals most of the data that we care about, but we still need to analyse the malicious zip, we can extract this using `ripmime`:

```Bash
unzip -l Invoice_2025_Payment_1.zip # View the file WITHOUT extracting it.
```

***

## Questions:

What does getting the IP and other data from the attack help?:
What is a Sender Policy Framework?:
Why is getting a SHA-256 hash of a file important?:

