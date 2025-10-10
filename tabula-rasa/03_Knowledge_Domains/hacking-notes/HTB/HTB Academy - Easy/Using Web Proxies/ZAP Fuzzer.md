---
title: 'ZAP Fuzzer:'
updated: 2023-08-12T14:08:00.0000000+01:00
created: 2023-08-12T13:03:06.0000000+01:00
---

Fuzzing with ZAP:

The **ZAP Fuzzer** is very powerful and isn't throttled like **Burp Intruder**.

To start our fuzzing, we need to send a request to the fuzzer, we can do this via right-clicking a request and sending it to **Attack\>Fuzz**:
![image1](../../../../_resources/image1-176.png)

We need to configure 4 options:
- Fuzz Location
- Payloads
- Processors
- Options

Locations:

The **Fuzz Location** defines our payload position, i.e. what we are fuzzing. To set up our location we **select a word** then **add** a payload:
![image2](../../../../_resources/image2-145.png)

Payloads:

ZAP fuzzer has similar payloads to **Intruder's Payloads**, though they are less advanced, we can click on the add button and select a payload, the most common are:

- **File**
  - *This selects a wordlist from file - the traditional fuzzing method.*
- **File Fuzzers**
  - This allows us to select wordlists from a built-in database of wordlists
- **Numberzz**
  - This generates a sequence of numbers with custom increments.

An advantage of **ZAP fuzzer** is that we don' need to provide our own wordlists - we can get databases from the **ZAP marketplace** - in this example we can select **File Fuzzers** as our type of payload and select the first wordlist from dirbuster.
![image3](../../../../_resources/image3-111.png)

Processors:

We can also perform some processing on each word in our payload wordlist. We can perform the following processes:

- Base64 Decode/Encode
- MD5 Hash
- Postfix String
- Prefix String
- SHA-1/256/512 Hash
- URL Decode/Encode
- Script

As we can see, we have a variety of encoders and hashing algorithms we can select. We can add custom strings before and after words using **Postfix String or Prefix String.** Finally, the **Script** option enables us to select a custom script that will run on every page.

We should use **URL encode** to make sure that our payload get properly encoded so that we can fuzz correctly without any server errors - We can also use the **generate preview** to see how our final payload will look:

![image4](../../../../_resources/image4-88.png)

Options:

Finally, we can configure our fuzzing options, we can set our **concurrent threads per scan** which will influence the speed of our scan - having threads at **20** means we will have a fast scan.
![image5](../../../../_resources/image5-68.png)

Importantly, we can choose either a **breadth-first search** which will use 1 keyword across all targets then move to the next word or a **depth-first search** which will use all keywords on the first target before moving to the next.

We can then start our attack and filter for 200 codes.

Task:
![image6](../../../../_resources/image6-46.png)

So we need to perform the following:

1.  Visit the /skills/ directory and get our cookie
2.  Place the request into the ZAP fuzzer
    1.  Use right-click Attack \> Fuzz
3.  Select the cookies request
    1.  Copy the set-cookie request
4.  Select the top-usernames-shortlist.txt wordlist
    1.  Hash these into md5 using the ZAP processor.
    2.  ![image7](../../../../_resources/image7-40.png)
5.  Start the attack.
    1.  We are looking for a response with a different response size:

*Note when we are sending cookies, we should sent them like so:*
![image8](../../../../_resources/image8-34.png)
**Cookie: Cookie Name=value**

This will give us the flag in request 8:
![image9](../../../../_resources/image9-29.png)

