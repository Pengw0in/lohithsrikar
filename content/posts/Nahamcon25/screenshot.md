+++
date = '2025-05-23T20:23:58+05:30'
draft = false
title = '[Nahamcon25] ScreenShot!'
series = 'nahamcon25'
featured_image = "/images/nahamcon/freeflags/featured.png"
tags = ['writeups']
+++

{{< series title="NahamCon 2025 CTF Series" series="nahamcon25" >}}

# ScreenShot!

Hello everyone!
Let's wrap this up quickly!

This is a CTF challenge from NahamCon 2025 where we are given an image.

<img src="/images/nahamcon/screenshot/1.png" alt="Challenge Screenshot" width="600">

Well, the image contains a hex dump of some zip file.

<img src="/images/nahamcon/screenshot/2.png" alt="Hex Dump Screenshot" width="600">

Well, how did I know it's a zip file? Well, obviously it's mentioned in the CTF description, right?

That's true, but another way is to match the file signature. Each file extension has its own file signature at the beginning of the file. For example, in this case we have `504b`, which is the file signature for zip files! More info about them here: [https://en.wikipedia.org/wiki/List_of_file_signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)

So what we will do is reverse this hex dump to convert it back into a zip file and open that zip, hoping that we would find a flag file in it!

First, let's copy the contents of this image to a text file, say `hdump.txt`:

```text
00000000: 504b 0304 3300 0100 6300 2f02 b55a 0000  PK..3...c./..Z..
00000010: 0000 4300 0000 2700 0000 0800 0b00 666c  ..C...'......fl
00000020: 6167 2e74 7874 0199 0700 0200 4145 0300  ag.txt......AE..
00000030: 003d 42ff d1b3 5f95 0314 24f6 8b65 c3f5  .=B..._...$..e..
00000040: 7669 f14e 8df0 003f e240 b3ac 3364 859e  vi.N...?.@..3d..
00000050: 4c2d bc3c 36f2 d4ac c403 7613 85af e4e3  L-.<6.....v.....
00000060: f90f bd29 d91b 614b a2c6 efde 11b7 1bcc  ...)..aK........
00000070: 907a 72ed 504b 0102 3f03 3300 0100 6300  .zr.PK..?.3...c.
00000080: 2f02 b55a 0000 0000 4300 0000 2700 0000  /..Z....C...'...
00000090: 0800 2f00 0000 0000 0000 2080 b481 0000  ../....... .....
000000a0: 0000 666c 6167 2e74 7874 0a00 2000 0000  ..flag.txt.. ...
000000b0: 0000 0100 1800 8213 8543 07ca db01 0000  .........C......
000000c0: 0000 0000 0000 0000 0000 0000 0000 0199  ................
000000d0: 0700 0200 4145 0300 0050 4b05 0600 0000  ....AE...PK.....
000000e0: 0001 0001 0065 0000 0074 0000 0000 00    .....e...t.....
```

To reverse the hex dump and convert it into a zip file, the following command can be used:

```bash
xxd -r hdump.txt > hdump.zip 
```

And then unzip the `hdump.zip`:

```bash
unzip hdump.zip
```

And that's it! We will get a flag file!

---
*Last edit: 24-05-2025*