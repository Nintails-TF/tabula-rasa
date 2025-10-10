---
title: Creating a dig script
updated: 2023-08-04T00:17:30.0000000+01:00
created: 2023-08-03T23:45:39.0000000+01:00
date modified: Thursday, May 16th 2024, 4:34:03 pm
---

Introduction:

The purpose of the script is given a list of sub-domains separated by a newline character. Perform a dig search in TXT mode to look for any Text within the zones.

1.  read -p is used to get user input and store it inside a variable
2.  we then loop for each line in the file
    1.  Then we perform a dig text search on each line
    2.  print the output to the console.

![image1](../../../_resources/image1-2.png)
