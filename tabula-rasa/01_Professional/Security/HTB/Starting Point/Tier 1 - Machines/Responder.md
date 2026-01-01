---
date created: Thursday, January 1st 2026, 2:28:14 pm
date modified: Thursday, January 1st 2026, 3:12:54 pm
---

# Responder:

**Type:** *Windows, Very Easy*
## Enumeration:

- `nmap -sC -sV --min-rate 5000 10.129.21.191`
	- `port 80/http/Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)`

When checking the website via a browser we are redirected to **unika.htb**, which results in us being unable to connect to the site. 

Need to add this to hosts:
```Bash
su # You need to be in root to actually modify hosts within pwnbox
sudo echo "10.129.21.191 unika.htb" >> /etc/hosts
cat /etc/hosts/ # Checking that the command worked.
ping unika.htb # Checking the name resolves
exit # Control+D also works, leave superuser state.
```

**This is a vital step for completing boxes.** HTB controls the lab environments and my machine doesn't know how to resolve `unika.htb -> 10.129.21.191` adding it to hosts, tells my system where to go.

Ensure that you either clean up, or respawn your own environment from time to time. As so you don't clog the hosts file with IPs that are getting re-used.

## Exploitation:

The challenge hints at viewing the page with different languages and then directly tells us about **[[../../../Frameworks/Attack Techniques/Web/LFI (Local File Inclusion)|LFI (Local File Inclusion)]]** within the URL parameter.

We can exploit this to view the hosts file within the server by performing the following:
```Bash
curl "http://unika.htb/index.php?page=../../../../../../../../windows/system32/drivers/etc/hosts"
```

(This can also be done via Burp suite or a regular web browser. It's good practice to store the payload in a simple command, so we can save the output and repeat it easily.)

Another vulnerability hinted at is a [[../../../Frameworks/Attack Techniques/Web/RFI (Remote File Include)|RFI (Remote File Include]], these are dangerous because they can lead to direct Remote Code Execution!
