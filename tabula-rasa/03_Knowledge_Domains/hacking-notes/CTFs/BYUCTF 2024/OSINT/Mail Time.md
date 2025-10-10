---
title: Mail Time
date modified: Friday, May 17th 2024, 5:30:06 pm
---

Within the folds of memory, a photograph holds the key to an address now obscured by time's veil. Yet, in this image lies the path to a vital correspondence. With your aid, let us decode the hidden coordinates within to ensure our message reaches its intended destination at the post office.

If you think you have the address correct and your native language is not English please open a ticket.

Enter the flag as the exact address listed by Google Maps.

Flag format - `byuctf{full address}`
***

### Looking at meta-data

We have an image, the first thing I'm thinking of is looking at the metadata of the image and searching for location.

```Bash
exiv2 gotmail.png 
identify -verbose gotmail.png 
```

As we can see, the metadata has been scrubbed in exiv2, the identify does show that the device used was apple. 

### Reverse image searching on google

1. We can navigate to: https://images.google.com/
	1. Then we can upload our image, but we don't see any results.
2. https://www.tineye.com/ | This does show that this photo was taken in the Falklands
	1. Stanley on the Falkland Islands
		1. ![[Pasted image 20240517172142.png]]

***
### Finding it on google maps:

This website also links to it on google maps:
https://www.falklandislands.com/things-to-do/shopping-in-the-falklands/falkland-post-service-limited-p678991


This is the exact location of it.
https://www.google.com/maps/place/StanleyPostOffice/@-51.7569928,-58.0453712,11.75z/data=!4m6!3m5!1s0xbe81d3aee45684f5:0x8192833eb1de20e3!8m2!3d-51.6914978!4d-57.864081!16s%2Fg%2F11kr_xgmvf?entry=ttu
