---
date created: Friday, November 21st 2025, 7:23:46 pm
date modified: Friday, November 21st 2025, 7:55:51 pm
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

