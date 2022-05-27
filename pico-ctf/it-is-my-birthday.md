---
description: 'Author: madStacks'
---

# It is My Birthday

### **Description**

I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website. [http://mercury.picoctf.net:11590/](http://mercury.picoctf.net:11590/)

## Solution

![](<../assets\_md/Pasted image 20220527091619.png>)

Since, Hash Algorithms generates non-reversable and unique strings for each input. So, getting same hash for two different files is impossible.

But since, `MD5` algorithm has been broken, so we can get same hash for two different files as discussed in [This article](https://www.mscs.dal.ca/\~selinger/md5collision/)

![](<../assets\_md/Pasted image 20220527141920.png>)

**Bypassing File Upload Check**

We are required to upload `pdf` file, to bypass the upload check we can change the extension of the downloaded file to `pdf`.

![](<../assets\_md/Pasted image 20220527142752.png>)

![](<../assets\_md/Pasted image 20220527142804.png>)

_**We Got The Flag, and Vulnerable Code**_

![](<../assets\_md/Pasted image 20220527142845.png>)
