---
title: Fake Smarties
date modified: Friday, May 17th 2024, 4:28:55 pm
---

Can you exploit the issues in my Machine Learning Model?

`nc fakesmarties.chal.cyberjousting.com 1359`

***

We are given a zip file **fake_smarties.zip** and we have a netcat to the system running on a server. The python script tries to figure out if a comment is liberal or conservative - if we can get a statement that is >100% liberal or conservative we get the flag:

``` python
if sim_conservative >= 1 or sim_liberal >= 1:
    print("Hmmmm, that doesn't seem right...")
    print(flag)
```

The problem with the program is that is evaluates the statements the wrong way. e.g. conservative statements are classified as being liberal.

```
Input a comment to test: donald trump freedom
Comment is Liberal: (118% confidence)
Hmmmm, that doesn't seem right...
byuctf{AI_1s_c00l_br0s}
```

You can come up with your own statements by looking at the file **make_model.py** which has some example statements that the model is using.


