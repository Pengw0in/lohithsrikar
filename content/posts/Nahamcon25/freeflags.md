+++
date = '2025-05-23T20:23:58+05:30'
draft = false
title = '[Nahamcon25] Free Flags!'
series = 'Nahamcon25'
featured_image = "/images/freeflags/featured.png"
tags = ['writeups']
+++

{{< series title="NahamCon 2025 CTF Series" series="Nahamcon25" >}}

# Free Flags!

Hello everyone!

<img src="/images/freeflags/1.png" alt="Challenge Screenshot" width="600">

This is our first challenge in NahamCon 2025 CTF. In this challenge, we are given a *free_flags.txt* file, which apparently contains a lot of flags! So how do we find the correct flag among them?

Brute force maybe? Perhaps?

Well, it's possible, but not feasible!

<img src="/images/freeflags/2.png" alt="File Contents" width="600">

So how do we solve this? If only we had criteria to filter out the correct flag... if only we had... wait! If you have read the rules properly, you'll find something like this:

```text
Flags for this competition will follow the format: flag{[0-9a-f]{32}}. 
That means a flag{} wrapper with a 32-character lowercase hex string 
inside—basically something that looks like an MD5 hash.
```

Yeah, these are the criteria we need! To be honest, all we need is this regex pattern: **`flag{[0-9a-f]{32}}`**

Let's write a small Python script to scan and filter the flag we need. Below is the Python script for this challenge:

```python
import re

with open('free_flags.txt', 'r') as f:
    flags = f.read()

flag = re.findall(r'flag\{[0-9a-f]{32}\}', flags)
print(flag)
```

Running this script will give us the flag we need!

**Author:** Zendex/Pengw0in