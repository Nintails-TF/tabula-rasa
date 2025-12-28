---
date created: Friday, November 21st 2025, 7:23:46 pm
date modified: Sunday, December 28th 2025, 4:17:10 pm
---

# Quick Notes:

**Meow:**
- `ping` - Used to test connection with a target using an ICMP (Internet Control Message Protocol).
- `nmap` - Used to test and find open ports on a target.
	- `Port 23/Telnet`: Telnet allows us to access terminals through a LAN or the internet, like SSH. But it is insecure and all data is transmitted in plaintext.
- `root` - The default admin name for a superuser in Linux.

**Fawn:**
- `Port 21/File Transfer Protocol`: FTP allows the transfer of computer files between computers using the client-server model. This is done in plaintext, so is not suitable for sensitive data.
	- `Port 22/Secure File Transfer Protocol`: SFTP is used for secure transfer of data between client and server.
	- So we can connect to FTP or SFTP servers and we are the client, or we can open our own FTP/SFTP server and clients can download the content we serve.
- `nmap -sV` - Probes open ports to determine service or version information.
	- FTP version: `vsftpd 3.0.3` is running on the Unix server.
- If we want to login without a username, we can try using username: `anonymous` when logging in with FTP.
	- `230` response code if successful login.
- We use `get` within the FTP context to download a file from the server to our local machine.

**Dancing:**
- `Port 445/SMB (Server Message Block)` Legacy devices can use different port numbers, but modern implementations use 445.
- We can use `smbclient` to search the SMB
	- `-L` flag lists shares
- To connect to a share: `smbclient //SERVER/SHARE`

**Redeemer:**
- `nmap -sV -p- --min-rate 5000 10.129.34.116` - Scan all ports (1-65535), Do so aggressively with 5000 packets per second.
	- In an actual engagement, this can flag IDS or cause network congestion (Higher Latency, Packet loss, connection timeouts.)
- A Redis database is running on port 6379
	- We can use `redis-cli` to interact with this.
	- Connecting to the Redis database port: `redis-cli -h HOSTNAME/IP`
- Retrieving DB info
	- `info` - returns information and stats about the server.
	- `select` - Enables us to select a database within Redis.
	- `KEYS *` - Returns all keys within a database.
	- `GET <Keyname>` - retrieves the string value associated with the key.

**Explosion:**
- Machine about Windows and **Remote Desktop Protocol** (RDP). **Telnet** was an old remote access tool that ran without encryption.
- `nmap -sV 10.129.19.14` - will reach port 3389 (Default port for RDP)
	- `-p 3389` - Would scan a single port.
	- `-p 1-1000` - Would scan ports 1-1000
	- `-p-` - Would scan all ports (65,535)
- Using FreeDRP we can connect to the remote machine
	- `xfreerdp /v:10.129.19.14:3389 /u:administrator /p:`
	- This gives us a desktop projection of the remote machine. As we login with administrator with a blank password.

**Preignition:**
- Linux Machine, refers to [[../../../Glossary#^DBF-def|Directory Brute Forcing/Dir Busting]].
- `Port 80/HTTP` found. Running `nginx 1.14.2`
- `gobuster dir -u http://10.129.19.17 -w /usr/share/wordlists/dirb/common.txt -x php`
	- `dir`: We are doing directory/file enumeration
	- `-u`: The URL target, needs `http://` or `https://`
	- `-w`: The path to the [[../../../Glossary#^wordlist-def|wordlist]]
	- `-x`: The file extension we're looking for. `.php` in this case.
- We can then navigate to the admin portal: `http://10.129.19.17/admin.php`
	- Log-in using `admin:admin`

**Mongod:**
- Linux Machine, refers to connecting to an unsecured MongoDB service.
- Need to scan all ports to view all TCP ports: `nmap -sV -p- --min-rate 5000 10.129.228.30`
	- `port 22/SSH` - OpenSSH 8.2p1 Ubuntu (Default Port)
		- Commonly targeted by brute-force attacks, needs key-based auth and you can consider placing this on a non-standard port too.
	- `port 27017/mongodb` - MongoDB 3.6.8 (Default Port)
		- Often left misconfigured and left exposed to the internet without authentication leading to data breaches.
			- See: <https://hackread.com/mongodb-database-expose-lead-gen-records/,> <https://www.netsec.news/verifications-io-mongodb-misconfiguration-exposed-2-billion-records/,> etc.
		- Attackers can use automated scanning tools to locate and find these misconfigurations.
- MongoDB is a NoSQL DB, meaning data is stored in a more flexible schema, rather than with keys and using SQL to search. MongoDB uses JSON-like documents (BSON) to store details.
- `mongosh` - Connect remotely to the DB
	- **ISSUE:** The `mongosh`command doesn't work because the hosted DB is too old.
	- **SOLUTION:** Use docker and host an older version of the `mongo` CLI tool.
		- `docker run -it --rm mongo:4.4 mongo --host 10.129.228.30 --port 27017`
- `mongosh` syntax
	- `show dbs` - show all DBs
	- `show collections` - show all collections (tables) in the current DB.
	- `db.flag.find()` - search all documents within the flag connection in the current db.

**Synced:**
- Linux, refers to [[../../../Glossary#^Rsync-def|Rsync]]
- Nmap (`nmap -sV -p- --min-rate 5000 10.129.19.35`)
	- `port 873/rsync/protocol version 31`
- `rsync` interacts with the remote host
	- `rsync -r --list-only rsync://10.129.19.35/`
	- We can see that there is a `public`share. Within this, we have flag.txt
- Downloading the flag: `rsync rsync://10.129.19.35/public/flag.txt ./`
	- Downloads flag to current working directory.
	- `cat`the flag

***

## Summary:

The main purpose of these modules was the following process:

1. Find something using Nmap (scanning tool).
2. Figure out how to interact with it using the corresponding tool.
	1. *Telnet, FTP/SFTP, SMB, Redis, RDP, Directory Brute Forcing HTTP, MongoDB, Rsync*
		1. Always working with insecure/default implementations.
			1. Anonymous logins enabled, etc.
	2. Learn some of the terminology behind these tools. 
3. How to use the tool to search/query/download a flag.