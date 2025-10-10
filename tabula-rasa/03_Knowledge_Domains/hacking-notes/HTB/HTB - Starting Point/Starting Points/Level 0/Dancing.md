---
title: Dancing
updated: 2022-08-24T20:38:36.0000000+01:00
created: 2022-07-26T18:35:52.0000000+01:00
---

What is the command we can use within the SMB shell to download the files we find?

We can use SMBclient that will allow us to connect to the SMB share.

As a legit user, we would login using our username and password. But we can check as an illegitimate user that Guest authentication or Anonymous authentication.

We can use the following command to try to log in.

![image1](../../../../../_resources/image1-54.png)

We need to select one of the shares to see if we can log in to them. Trying every share, finally the WorkShares share is accessible without inputting a password.

![image2](../../../../../_resources/image2-40.png)

We then find the flag inside the James.P directory.

![image3](../../../../../_resources/image3-33.png)

I don't know where these files are stored though once I download them using get, which is the main issue.

**The files are place in the directory In which you run the smbclient. So In my case they are located at the root of the file system:**

![image4](../../../../../_resources/image4-25.png)

What does the 3-letter acronym SMB stand for?

*SMB stands for Server Message Block. It is a communication protocol and was developed in 1983 by Barry Feigenbaum. It is used to provide shared access to files and printers across nodes on a network of systems.*

*SMB is a primary attack vector in intrusion attempts and it was used in the 2014 Sony pictures attack and in WannaCry.*
What port does SMB use to operate at?

*SMB uses port 445 normally.*
What is the service name for port 445 that came up in our Nmap scan?

*The service name is "Microsoft-ds" at port 445.*
What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?

*We can use -l to list the contents.*

What is the name of the share we are able to access in the end with a blank password?

*WorkShares is the share we can access with an empty password.*
![image5](../../../../../_resources/image5-16.png)
What is the command we can use within the SMB shell to download the files we find?

*The command we use is get. It allows us to download the contents of the chosen directory.*

5f61c10dffbc77a704d76016a22f1664
![image6](../../../../../_resources/image6-9.png)
