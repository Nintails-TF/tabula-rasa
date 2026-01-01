---
date created: Monday, December 29th 2025, 5:07:38 pm
date modified: Thursday, January 1st 2026, 1:57:47 pm
---

# Quick Notes:

****

### Appointment:
- Linux, SQL injection introduction.
	- A03:2021 – Injection | Top 1 in 2017, Top 3 in 2021, Top 5 in 2025
- Nmap (`nmap -sV -p- --min-rate 5000 10.129.20.14`)
	- `port 80/http/Apache httpd 2.4.38 ((Debian))`
	- HTTPS defaults to port 443
- SQL
	- MySQL specific commenting using `#`, generally we use `--` for comments as that's language independent.
- SQLi payload: `admin'#`, The password check gets commented out, so we can login as admin without authentication.

***

## Sequel:
- Linux, more SQL and interacting with DBs
- Nmap (`nmap -sV -p- --min-rate 5000 10.129.21.188`)
	- Scan took 200 seconds, quite long: `port 3306/mysql/MySQL 5.5.5-10.3.27-MariaDB-0deb10u1`
- Connecting to MariaDB
	- `mysql -h hostname/IP -u username` - By default the username is **root** with no password.
- Interacting with MariaDB
	- We can perform queries within SQL on the data, so `SHOW DATABASES;` would give us all the DB names.
	- By default you have three default DBs: `information_schema, mysql, performance_schema`
		- In this task, we have a `htb` database which contains the flag.
- Interacting with a database
	- `USE htb;` - Select our DB
	- `SHOW TABLES;` - Display the tables
	- `SELECT * FROM table_name;` - Query the tables for all data

***

## Crocodile:

- Nmap (`nmap -v -sV --min-rate 5000 10.129.1.15`)
	- We can use the flag `-sC` to define default scripts.
		- The default scripts within nmap are somewhat safe, they are non-intrusive, but could be logged or noticed.
		- Commonly, `nmap -sC -sV 102.168.1.1` is used as a solid baseline for recon.
			- Other scripts like `intrusive, vuln, exploit, brute` can be used.
	- `port 21/ftp/vsftpd 3.0.3` - Very Secure FTP daemon: an FTP server for UNIX systems
	- `port 80/http/Apache httpd 2.4.41 ((Ubuntu))`
- FTP Login (`ftp 10.129.1.15`)
	- The `220` code means that the server is ready for a new user and is awaiting commands. `230` denotes a successful login. (username: anonymous)
	- You could write a script which would try login to any FTP servers and to search for these codes.
- FTP file exfiltration
	- `get allowed.userlist & allowed.userlist.passwd` - We get the usernames and passwords from the FTP server.
- Directory Brute Forcing (`gobuster dir -u http://10.129.1.15 -w /usr/share/wordlists/dirb/common.txt -x php`)
	- We see access to various `.php` files, of most promising is the `login.php`
	- We can login with the credentials we've gained from the FTP server.






