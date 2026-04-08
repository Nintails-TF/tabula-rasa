---
date created: Sunday, December 29th 2024, 12:04:59 pm
date modified: Sunday, January 5th 2025, 7:01:23 pm
Parent Link: "[[02_Professional/Career/Security/Index|Security Index]]"
---

# Introduction:

As the world becomes more digitised, more and more capital is being placed into technology, computers and electronics. Hackers are those who understand and manipulate these tools.

*In a world where ever company, corporation, organisation and the collective majority control you through the reins of technology, the art of hacking gives the individual freedom to pursue goals and enact change.*

Mastery of Linux along with other core IT components is key to understanding the art of hacking.

Other cores concepts include:
1. Networking Fundamentals
2. Programming and Scripting
3. System architecture and administration
4. Cryptography and security concepts
5. Security testing methodology
6. Web security

Certain other topics such as IoT (Internet of things) and leveraging AI have been and will continue to grow in popularity and become more relevant, but aren't at the backbone of IT.

The chapters are structured like so:
- Chapter 1 - File system and terminal basics.
- Chapter 2 - Find, examine and alter software and files.
- Chapter 3 - Managing and scanning networks.
- Chapter 4 - Streamlining your system and managing software.
- Chapter 5 - File and directory permissions.
- Chapter 6 - Managing services, processes and resources.
- Chapter 7 - Managing environment variables.
- Chapter 8 - Bash Scripting.
- Chapter 9 and 10 - File system management.
- Chapter 11 - Introduction to logging.
- Chapter 12 - Apache, OpenSSH and MySQL.
- Chapter 13 - Proxies, TOR, VPNs and encrypted email.
- Chapter 14 - Wireless networks.
- Chapter 15 - The Linux kernel.
- Chapter 16 - Scheduling in Linux.
- Chapter 17 - Python concepts and projects.

Ethical hacking is the practice of exploiting a system to better secure it by finding vulnerabilities. 

For anything to be useful, it **must** be replaceable. For this reason, PoCs (Proof of Concepts), clear and concise explanations with solid documentation is key.

## Brief Summary:
- Learning Linux requires knowledge of a few essential topics; networking, scripting, system architecture and secure practices.
- Hacking is a form of freedom and artistic expression.
- Concise and clear documentation is necessary, as it provides a guide on how to repeat any sort of hack or technique.

***

# Chapter 1 - Getting Started with the Basics:

Hacking is that act of manipulating things, usually technology.

## Terms and Concepts:

There are a few primary concepts to know when using the Linux terminal.

1. **Binaries**
	1. *Binaries refers to programs that can be executed, these are usually stored in the `/usr/bin` and `/usr/sbin`.*
	2. A program can be made into a binary using `chmod +x filename`
2. **Directories**
	1. *Directories are folders and are used to organised files in a hierarchical manner.*
3. **Home**
	1. *Each user has a `/home` directory. The files they create will usually be stored here.*
4. **Root**
	1. *This is the superuser account, who can do pretty much everything on the system.*
		1. *This is much different than Windows, where Linux **WILL allow you to brick your system** if you command it to, so you have to be careful.*
5. **Script**
	1. *A series of commands that use an interpreter to run source code. Some hacking tools are just scripts, scripts can be run with the bash interpreter or any other scripting languages (Python, Ruby, Perl, etc).*
6. **Shell**
	1. *The shell is the environment and interpreter for running commands in Linux, the most widely used shell is **Bash (Bourne-again shell)**. [C shell and Z shell (csh and zsh)](https://www.howtogeek.com/68563/htg-explains-what-are-the-differences-between-linux-shells/) are also popular options.*
7. **Terminal**
	1. *The CLI interface that is used to enter commands into the shell.*

## The Linux File System:

Linux uses a virtual drive which is partitioned upon a physical hard drive, this is because originally, you had many users sharing the same PC simultaneously. The root or `/` of the file system and is the top of the tree.

![[Pasted image 20241229173130.png]]

**Always start programs as a regular user, rather than as a super user, unless you need the privileges.**

## Basic Commands in Linux:

### Basics:
``` Bash
pwd # "Present Working Directory" returns your current location in the directory.
whoami # Tells you what user you are logged in as.
cd /etc # Changes your current directory to that of /etc (store config files).
cd .. # Moves up a single level in the file structure.
cd .. .. # Moves up two levels, triple dots would move up 3, etc.
cd / # Moves you to root.
ls # Lists the contents of a directory.
```

### Listing Files:
```Bash
ls -l # The long flag shows permissions, owner, size and last modified date.
ls -a # Shows hidden files, you can combine flags like so: ls -la.
```

### Extra - How to Read long Outputs:
![[Pasted image 20241231095324.png]]
### Getting Help:
```Bash
nmap --help # --help is a word option.
nmap -h # -h is a single letter option.
man nmap # all of these help options basically do the same thing, give you help.
```

### Finding Stuff:

There are a few different ways of searching your file system. Each with certain advantages and disadvantages:

```Bash
locate aircrack-ng
```

The locate method searches your entire file system and locates every occurrence of a word, in this case *aircrack-ng.* Locate has a few drawbacks:

1. Locate can give too much information.
2. Locate's database is only updated once per day, making it ineffective for new files.

```BASH
whereis aircrack-ng
```

The `whereis` command returns the binaries and manual pages of the searched term, making it more concise than locate.

```Bash
which aircrack-ng
```

We can think of the `which` command as a more specific `whereis`, it only cares about binaries which are in the PATH. 

### Finding Stuff for Real:

```Bash
find directory options expression # This is the general syntax for find.
find / -type f -name apache2 # Start from root, look for files, called apache2.
find /etc -type f -name apache2 # Start searching from /etc instead of root.
```

Find is the grandfather of searching utilities. It is powerful and flexible, you have to be careful not too be too broad with your starting directory, since starting too far out will take a long time to search every directory.

We can speed up searches by using our knowledge of the Linux file system. Where we only search sub-directories where we would expect our file/directory to be in. (/etc for config files, /bin /sbin or /lib for binaries).

The quirk with find is that it **only display exact name matches.** This means if we wanted to search for the file name of `apache2.conf` we wouldn't find a match. This can be remediated with the use of wildcards.

### Finding with Wildcards:

```Bash
find /etc -type f -name apache2.* # Search for apache2 with any file extension.
```

There are three main types of wildcard - but by far the most commonly used is the `*`.
- `?`
	- The question mark wildcard is used to represent a single character.
	- The search of `find ?at` would find *cat and rat* but not *what.*
- `[ ]`
	- The square brackets wild card is used to represent a list of characters.
	- The search of `find [c,b]at` would find *cat and bat* but not *rat or what.*
- `*`
	- The asterisk searches for characters of any length, including none or an unlimited length.
	- The search of `find *at` would find *cat, bat, rat and what.*

### Filtering Results Using Grep:

Usage of `grep` is very helpful when we want to filter any sort of command line output for particular keywords. We pipe the output of a command using the `|`character to send the output as the input into grep.

```Bash
ls -la | grep "Papers" # Lists directory contents and filters for "Papers".
ps aux # Lists all system processes that are running.
ps aux | grep apache2 # Lists any system process with "apache2" in it.
```

### Modifying Files and Directories:

There are a few different methods of creating files in the Linux terminal:
```Bash
cat > my-file # A file called my-file is created then you can type text into it.
cat >> my-file # A double arrow denotes an append to the file.
# Use CTRL+D to save your output to file.
touch my-file # This creates a new empty file.
mkdir my-directory # This creates a new empty directory.
cp oldfile /home/my-directory/newfile # Copyies data from old to new location.
mv newfile newfile2 # Renames a file using the move command.
rm newfile2 # Deletes the named file.
rmdir my-directory # Will delete an empty directory.
rm -r my-directory # Will delete a non-empty directory. BE CAREFUL, YOU CAN DELETE KEY SYSTEM FILES BY MISTAKE USING THIS TECHNIQUE.
```

## Brief Summary:
- Linux uses a hierarchical file system with root (/) at the top.
- Essential concepts: Shell, Terminal, Root, Binaries, Scripts.
- Basic commands focus on navigation (`pwd, cd, ls`), file operations (`touch, mkdir, cp, mv, rm`), and searching (`find, grep`).

**Completion Time:**
*182 Minutes for Intro/CH1*
*7.3 Pomodoro cycles*

***

# Chapter 2 - Text Manipulation:

## Intro:

In Linux, everything is a file and frequently we deal with text files, so having a strong understanding of how we can manipulate, filter and search files is crucial. 

This enables us to reconfigure applications, search for system logs, and filter outputs for meaningful data. In the following examples, we will be reading files from [**Snort**](https://www.snort.org/) a widely used IDS (Intrusion Detection System).

## Viewing Files:

The `cat` command has a few shortcomings. In that it will print the whole stream of the file to the terminal, where in some-cases we don't need that much content.

```Bash
cat /etc/snort/snort_defaults.lua  # From CH1

# head and tail both default to showing 10 lines.
head -20 /etc/snort/snort_defaults.lua  # head shows first 20 lines of a file.
tail -20 /etc/snort/snort_defaults.lua  # Tail shows last 20 lines of a file.

"""
With longer files, we could find it useful to display how many lines a file has, so we can hop to a specific point and check for any changes.
"""
# We can see from nl, that our file has 1173 l;ines, making referencing a specific line easier.
nl /etc/snort/snort_defauls.lua 
> ...SNIP ...
> 1173  snort_whitelist_append(default_whitelist)
```

## More Filtering with Grep:

By in large `grep` is the most indispensable tool used in the art of text manipulation.

```Bash
# Display all lines that have the word output 
cat /etc/snort/snort.conf | grep output 

"""
Challenge show 5 lines below '-- default js_norm configuration'
"""

# My solution uses the -A flag in grep. We can use -A or -B to get lines before or after by a specified amount.
nl /etc/snort/snort_defaults.lua | grep -A 5 "default js_norm"

# Book solution, Start tail at the line of the phrase and pipe it into head to return the top 6 lines.
tail -n+507 /etc/snort/snort_defaults.lua | head -n 6
```

## Using the Stream Editor (`sed`):

The stream editor is similar to grep, where it searches for an occurrence of a word or pattern then performs an action on it.

For example:
```Bash
sed s/mysql/MySQL/g /etc/snort/snort.conf > snort2.conf
```

 *For string `mysql` replace it with `MySQL`globally (all occurrences) in the snort.conf file, save the output to the snort2.conf file.

`sed` can also work to replace **specific occurrences** of a phrase:
```Bash
sed s/mysql/MySQL/ snort.conf > snort2.conf # Replace only the first instance .
sed s/mysql/MySQL/2 snort.conf > snort2.conf # Replace only the 2nd instance.
```

## Viewing Files with More and Less:

When we use `cat` we scroll to the end of a file. Sometimes if we want to scour a file we can use other commands like `more` and `less`.

```Bash
# more displays one page of a file at a time. q to quit,
more /etc/snort/snort.conf
# less displays one page at a time and allows you to filter for terms.
less /etc/snort/snort.conf
```

You can filter using less using the `\` delimiter and by searching for a pattern or word. You can use `n` to go forward and `N` to go back. You can use the `-i` flag and then use regular expressions to search case-insensitively:

```Bash
less -i file.txt
> /\<rules\> # Will search for all instances of rules.
```

## Brief Summary:
- Text manipulation is a key skill in Linux, particularly the usage of `grep`.
- You can read/output portions of a file using either `head` or `tail`. Depending if the content you seek is at the start or the end of the file.
- `more` and `less` are valuable tools in reading files interactively - with more being used to plain reader and less being used for additional searching functions.
	- *less is more*

**Completion Time:**
*75 Minutes for chapter 2 notes*
*3 Pomodoro cycles*

***

# Chapter 3 - Analyzing and Managing Networks:

## Introduction:

Knowledge of networking is essential for hacking, as being able to navigate the sea of networks enables you to understand and access the resources you need.

At times, it may be necessary to:
- Connect to a computer with your IP address hidden from view.
- Redirect DNS queries from a target to your machine.
- Spoofing your MAC address to prevent being restricted or blocked.

In essence, we can say that networking is the road and car that lead to the destinations that we want to access, if our car isn't fit for the job then we can change it, if the road is bumpy we find a new way.

## Analyzing Networks:

`ifconfig` is one of the most basic tools to examine any active network interfaces.

```Bash
ifconfig
...SNIP...
# We can see an example of an active network interface wlan0:
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.66  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e86c:e5ea:6838:3dae  prefixlen 64  scopeid 0x20<link>
        ether b8:9a:2a:08:a5:d4  txqueuelen 1000  (Ethernet)
        RX packets 6665786  bytes 9002500896 (8.3 GiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 471790  bytes 128461439 (122.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0   
```

### Explaining `ifconfig` Output:

| **Property**          | **Value**                           | Purpose                                                                                                                        |
| --------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Interface Name**    | `wlan0`                             | Name of our wi-fi adapter. Note that Linux starts counting at 0.                                                               |
| **Flags**             | `UP, BROADCAST, RUNNING, MULTICAST` | Tells us what communication methods are possible with our adapter.                                                             |
| **MTU**               | `1500`                              | The **Maximum Transmission Unit** is the largest packet size (in bytes) that can be transmitted in a single frame.             |
| **IPv4 Address**      | `192.168.1.66`                      | The IP address assigned to our NIC.                                                                                            |
| **Subnet Mask**       | `255.255.255.0`                     | Determines if an IP address is **external** or **local**. Splits an IP address into two parts: **Network ID** and **Host ID.** |
| **Broadcast Address** | `192.168.1.255`                     | An address used to send messages to all devices in the subnet.                                                                 |
| **IPv6 Address**      | `fe80::e86c:e5ea:6838:3dae`         | The IPv6 address assigned to our NIC.                                                                                          |
| **Prefix Length**     | `64`                                | Represents the size of the network portion of an IP address in CIDR notation.                                                  |
| **Scope ID**          | `0x20<link>`                        | Defines the scope or range of an IPv6 address's usability. e.g. only valid within our same physical or logical link.           |
| **MAC Address**       | `b8:9a:2a:08:a5:d4`                 | The MAC address of our network adapter.                                                                                        |

## Checking Wireless Network Devices:

`iwconfig` is used by wireless adapters to gather info from wi-fi adapters, it is particularly important when using wireless hacking tools like `aircrack-ng`.

```Bash
iwconfig
# This shows our routers infomration.
wlan0     IEEE 802.11  ESSID:"BT-JQA268"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 4C:1B:86:D0:00:06   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1771   Missed beacon:0
```

### Explaining an `iwconfig` Output:

| **Property**             | **Value**                  | **Description**                                                                                     |
|--------------------------|----------------------------|-----------------------------------------------------------------------------------------------------|
| **Interface Name**       | wlan0                     | The wireless network interface being monitored.                                                    |
| **ESSID**                | BT-JQA268                 | The name of the connected Wi-Fi network.                                                          |
| **Mode**                 | Managed                   | The interface is acting as a client connecting to an access point.                                 |
| **Frequency**            | 5.18 GHz                  | The frequency band used for communication. 5 GHz offers faster speeds but shorter range.           |
| **Access Point**         | 4C:1B:86:D0:00:06         | The MAC address of the access point (router) the interface is connected to.                        |
| **Bit Rate**             | 1 Mb/s                    | Current data transmission rate. Low rate indicates potential issues like interference.             |
| **Tx-Power**             | 22 dBm                    | Transmission power of the wireless interface (22 dBm = ~158 mW).                                   |
| **Retry Short Limit**    | 7                         | Maximum number of retransmission attempts for a short packet before it’s dropped.                  |
| **RTS Threshold**        | Off                       | RTS/CTS is disabled, meaning no additional checks to reduce collisions in the network.             |
| **Fragmentation Threshold** | Off                    | Packet fragmentation is disabled, meaning packets are sent in full.                                |
| **Power Management**     | On                        | Power-saving mode is enabled to conserve energy.                                                   |
| **Link Quality**         | 51/70                     | A measure of signal quality (~73%). Indicates decent connectivity.                                 |
| **Signal Level**         | -59 dBm                   | Strength of the received signal. -59 dBm is considered strong.                                     |
| **Rx Invalid Nwid**      | 0                         | No packets received with an invalid network identifier (SSID mismatch).                            |
| **Rx Invalid Crypt**     | 0                         | No packets received with encryption errors (e.g., incorrect password or corruption).               |
| **Rx Invalid Frag**      | 0                         | No packets received with incorrect fragmentation.                                                  |
| **Tx Excessive Retries** | 0                         | No transmission attempts failed after exceeding retry limits.                                      |
| **Invalid Misc**         | 1771                      | Count of miscellaneous invalid packets. A high value may indicate interference or hardware issues. |
| **Missed Beacon**        | 0                         | No beacon frames from the access point were missed, indicating stable communication.               |

## Changing Your Network Info:

Modifying your IP address is a very useful skill because by spoofing your IP you protect yourself from being captured during forensic analysis and blocked by CDNs.

You can use IP spoofing in DoS (Denial-of-service) attacks to make it look like your IP is coming from somewhere else. 
### Changing Your IP Address:

`ifconfig` can be in combination by the interface name and the new IP address you want assigned to the address.

```Bash
ifconfig wlan0 192.168.181.115
```

To check that the assignment worked as expected you can check `ifconfig` again to see your new IP.
### Changing Your Network Mask and Broadcast Address:

`ifconfig` can be used in a similar way to modify your network mask and broadcast address

```Bash
ifconfig eth0 192.168.181.115 netmask 255.255.0.0 broadcast
192.168.1.255
```

You change the network mask in order to expand or shrink the **network ID** or **host ID.** e.g. we can change the host portion from (/24) to (/23). Alternatively you can also create more/less subnets to isolate traffic, enhance performance or simplify network management.

Broadcast address is changed to match the size of the network mask.
### Spoofing Your MAC Address:

`ifconfig` is used to change your MAC address. The MAC address is a globally unique value and is used to trace or block hackers from networks. Changing your MAC address can bypass network access controls.

When spoofing your MAC address, you need to do the following:
```Bash
"1. Take your interface down (eht0, wlan0, etc.)"
ifconfig wlan0 down
"2. Modify the network adapters ether"
ifconfig wlan0 hw ether 00:11:22:33:44:55
"3. Bring your connection back online."
ifconfig wlan0 up
```

Have a final check using `ifconfig` and you should see that your MAC address has changed.

### Assigning New IP Addresses:

The daemon that runs called `dhcpd`*DHCP daemon.* This process often runs in the background within servers to handle DHCP requests to manage IP addresses.

The DHCP (Dynamic Host Configuration Protocol) daemon assigns IP addresses to all the systems on the subnet and logs which IP is assigned to which machine, this can enable forensic analysis to trace any attackers, so we need to understand about how DHCP works.

If we want to connect to the internet from our LAN (Local Area Network) we need to have our IP assigned by DHCP, since ISPs have pools of IP addresses that they assign to customer routers, basically this means if we want a new IP we need to request a new IP from DHCP.

We could use a static IP if we configured our router correctly with a public IP.

We do this in Linux by using the `dhclient` so that we can send a `DHCPDISCOVER` request to our network interface (usually either `eth0` or `wlan0`). 

Our DHCP server running from our router then sends `DHCPOFFER` back to our client and gives us available IP address and configuration details.

Our client then accepts the request using `DHCPREQUEST`

Finally, the server will acknowledge our request and assign us the IP address using `DHCPACK`

This will give us a new IP address, broadcast address and netmask for our network interface. When we get a new IP address, we can get assigned the same IP unless it is already in use or the lease expires.
## Manipulating DNS:

If you are attacking a target, you can look at DNS info to glean valuable information for further exploitation.

### Digging the DNS:

We can use `dig` to gather DNS information about a target domain, giving us an essential piece of early reconnaissance.

### Changing Your DNS Server:

We modify our `/etc/resolv.conf` file on system.

### Mapping Your IP Address:

The special file on our system called the `hosts` is used in IP address translation.

## Brief Summary:

- We can use `ifconfig` to examine our networks details and modify them to bypass common security measures.
- We can use `iwconfig` to gather information about
