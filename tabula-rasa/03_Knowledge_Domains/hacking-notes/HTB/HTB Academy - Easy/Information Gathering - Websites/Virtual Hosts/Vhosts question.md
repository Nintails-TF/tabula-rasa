---
title: 'Vhosts question:'
updated: 2023-08-05T04:11:48.0000000+01:00
created: 2023-08-05T03:57:12.0000000+01:00
---

Virtual Hosts Flags:

- Flag 1:
  - HTB{h8973hrpiusnzjoie7zrou23i4zhmsxi8732zjso}
- Flag 2:
  - HTB{u23i4zhmsxi872z3rn98h7nh2sxnbgriusd32zjso}
- Flag 3:
  - HTB{Fl4gF0uR_o8763tznb4xou7zhgsniud7gfi734}
- Flag 4:
  - HTB{bzghi7tghin2u76x3ghdni62higz7x3s}
- Flag 5:
  - HTB{7zbnr4i3n7zhrxn347zhh3dnrz4dh7zdjfbgn6d}
We can scan for vhosts in ffuf using:
![image1](../../../../../_resources/image1-158.png)

![image2](../../../../../_resources/image2-128.png)

In order to access any of these pages, we need to add them to the hosts file:
![image3](../../../../../_resources/image3-99.png)

To get our flags, we need to look at each of these virtual hosts.
