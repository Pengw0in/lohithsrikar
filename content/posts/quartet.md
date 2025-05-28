+++
date = '2025-05-28T20:23:58+05:30'
draft = false
title = 'Quartet'
+++

# Quartet

Hewo people!

So in this writeUp, lets see how we can solve this Quartet CTF from NahamCon2025.

<img src="/images/quartet/1.png" alt="1.png" width="600">

so we are given Four files with strange extension ? Well they maybe strange for a person who saw them for first time, but they are not!

These files with “zX”(where X is some number) extension are parts of a single zip file( .zip). so basically combining these zip files will give a one single complete zip file in theory.

Lets try to combine them with the following prompt 

```bash
 cat * > main.zip # make sure that all these files are in an isolated folder!
```

now lets unzip this main.zip file!

```bash
unzip main.zip
```

and Alas!, we are greeted with a error , which is just a warning🤷‍♂️

```bash
Archive:  main.zip
warning [main.zip]:  zipfile claims to be last disk of a multi-part archive;
  attempting to process anyway, assuming all parts have been concatenated
  together in order.  Expect "errors" and warnings...true multi-part support
  doesn't exist yet (coming soon).
warning [main.zip]:  1526784 extra bytes at beginning or within zipfile
  (attempting to process anyway)
file #1:  bad zipfile offset (local header sig):  1526788
  (attempting to re-compensate)
  inflating: quartet.jpeg
```

mehh , just ignore them. We can see that  *inflating: quartet.jpeg i*n the last, that mean a jpeg file is extracted from main.zip. Lets look at it.

<img src="/images/quartet/quartet.jpeg" alt="quartet.jpeg" width="600">

Woah a quartet! no wonder the ctf name is also the same. well it is a image lets search for strings and filter them out with following command

```bash
strings quartet.jpeg | grep "flag"
```

and there you go , the flag will appear!.