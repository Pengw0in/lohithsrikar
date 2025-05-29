+++
date = '2025-05-28T20:23:58+05:30'
draft = false
title = 'Quartet'
+++

# Quartet

Hello everyone!

In this writeup, let's see how we can solve the Quartet CTF challenge from NahamCon 2025.

<img src="/images/quartet/1.png" alt="Challenge Screenshot" width="600">

We are given four files with strange extensions. Well, they may seem strange for someone who's seeing them for the first time, but they're not!

These files with "zX" (where X is a number) extensions are parts of a single zip file (.zip). Basically, combining these zip files will give us one single complete zip file in theory.

Let's try to combine them with the following command:

```bash
cat * > main.zip # Make sure all these files are in an isolated folder!
```

Now let's unzip this main.zip file:

```bash
unzip main.zip
```

And alas! We are greeted with an error, which is just a warning 🤷‍♂️

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

Meh, just ignore them. We can see `inflating: quartet.jpeg` at the end, which means a JPEG file is extracted from main.zip. Let's look at it.

<img src="/images/quartet/quartet.jpeg" alt="Quartet Image" width="600">

Woah, a quartet! No wonder the CTF name is the same. Well, it's an image. Let's search for strings and filter them out with the following command:

```bash
strings quartet.jpeg | grep "flag"
```

And there you go—the flag will appear!