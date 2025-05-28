+++
date = '2025-05-28T20:23:58+05:30'
draft = false
title = 'Free Flags!'
+++

# Free Flags!

Hola people!

<img src="/images/freeflags/1.png" alt="1.png" width="600">

This is our first challenge in Nahamcon2025 CTF. In this challenge, we are give a *free_flags.txt,* which apparently contains a lot of flags! So how do we find the correct flag out of em?

Brute force maybe? maaaybee? 

well its a possible, but not feasible!

<img src="/images/freeflags/2.png" alt="1.png" width="600">

so so how? only if we have a criteria to filter out correct flag ….. only if… wait! if you have read the rules properly I think you can find something like 

```Text
Flags for this competition will follow the format: flag\{[0-9a-f]{32}\}. 
That means a flag{} wrapper with a 32-character lowercase hex string 
inside—basically something that looks like an MD5 hash. 
```

yeah, these are criterias we need, and to be honest all we need is this regex pattern ***flag\{[0-9a-f]{32}\} .*** 

So lets write a small python script to scan and filter the flag we need , below is the python script we need for this challenge 

```python
import re

with open('free_flags.txt', 'r') as f:
	flags = f.content()
flag = re.findall(r'flag\{[0-9a-f]{32}\}' , flags)
print(flag)
```

running this script will give us the flag we need!!\

Author : Zendex/Pengw0in