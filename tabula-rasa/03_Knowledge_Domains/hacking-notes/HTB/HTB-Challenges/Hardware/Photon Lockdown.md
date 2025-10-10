---
title: Photon Lockdown
date modified: Monday, May 13th 2024, 9:34:02 pm
---

## Introduction:

***CHALLENGE DESCRIPTION**

*We've located the adversary's location and must now secure access to their Optical Network Terminal to disable their internet connection. Fortunately, we've obtained a copy of the device's firmware, which is suspected to contain hardcoded credentials. Can you extract the password from it?*

We are given a file called **ONT**, which contains 3 different files:
1. fwu_ver
	1. This is ASCII text
		1. Catting this reveals that version 3.0.5 is running
2. hw_ver
	1. This is X1 archive data
		1. This is data from the X1 archive appliance, it looks like some kind of device information from XenData LTO.
			1. LTOs being a Linear Tape-Open tape drive which is used to store large amounts of data. Bit like a hard-drive.
		2. https://xendata.com/products/x1-archive-appliance-lto/
3. rootfs
	1. This is a Squashfs file system.
		1. Squashfs is a file system that is read-only, so I assume it has been used with this LTO to mange data.
		2. https://en.wikipedia.org/wiki/SquashFS
	2. 

A good first start is to setup squashfs-tools and to try and read the archive data using said tool to decompress it so that we can read it for some password information.

```Bash
git clone https://github.com/plougher/squashfs-tools.git
unsquashfs -ll rootfs # Shows us the file-system without dumping it.
```

We can then mount this to our system so that we can then search and analyse it:
```Bash
sudo mkdir /mnt/squashfs
sudo mount -t squashfs -o loop /path-to-file/rootfs /mnt/squashfs
```

Since, we want to find a password, we can use grep recursively on the file system to check for any hardcoded passwords:
``` Bash
grep -r PASSWORD

...SNIP...
etc/config_default.xml:<Value Name="WLAN1_ACCOUNT_RS_PASSWORD" Value=""/>
etc/config_default.xml:<Value Name="SUSER_PASSWORD" Value="HTB{N0w_Y0u_C4n_L0g1n}"/>
etc/config_default.xml:<Value Name="CWMP_ACS_PASSWORD" Value="password"/>
...SNIP...

```