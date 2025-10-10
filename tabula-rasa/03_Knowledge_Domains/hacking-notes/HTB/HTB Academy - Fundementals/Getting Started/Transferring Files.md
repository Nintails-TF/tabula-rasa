---
title: 'Transferring Files:'
updated: 2022-12-18T19:18:59.0000000+00:00
created: 2022-10-18T18:23:16.0000000+01:00
---

Intro:

During a penetration job, you will likely need to transfer files to a remote server. Such as enumeration scripts, exploits or transferring data back to our host.

We can use **Metasploit** and **Meterpreter** and use the *Upload* command to upload files, however, we still need to learn these methods for any reverse shells.

Wget:

The first method we can use to accomplish this is hosting a Python HTTP server and then using *wget* or *cURL* to download a file to the remote host. The way in which we do this is via:

1.  Go to the directory in which we want to save a file to.
2.  Load up our Python HTTP server:
    1.  ![image1](../../../../_resources/image1-79.png)
3.  Now that we have our listening server, we use wget on the remote host:
    1.  ![image2](../../../../_resources/image2-61.png)
4.  If *wget* doesn't work, we can use *cURL* instead:
    1.  ![image3](../../../../_resources/image3-53.png)
    2.  Note that we use *-o* to define the output name of the file (linenum.sh)

SCP:

Another method to transfer files is using the *scp* command. For this we do need **ssh credentials.** We simply do:
![image4](../../../../_resources/image4-44.png)

Base64:

If for some reason we can't transfer a file due to a firewall protection, we can encode a binary file/executable in base64.

So if we have a file named **shell** we can encode it:
![image5](../../../../_resources/image5-33.png)

Then we can decode it on our remote host:
![image6](../../../../_resources/image6-23.png)
Validating files:

To make sure we have the same file, we can use the **file** command:
![image7](../../../../_resources/image7-19.png)
When using the base64 method or any other encoder/decoder, we can validate the file using **md5sum**:
![image8](../../../../_resources/image8-17.png)

Then we compare the md5 on the remote server:
![image9](../../../../_resources/image9-16.png)

