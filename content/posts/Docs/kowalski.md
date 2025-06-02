+++
date = '2025-06-01T20:23:58+05:30'
draft = false
title = '[Docs] Kowalski - Discord bot'
featured_image = "/images/kowalski/featured.png"
tags = ['Documentation']
+++

# Kowalski Documentation
Kowalski is a simple bot written in python. This bot allows users to apply various encryptions , hashing methods and perform simple text analysis. This includes Caesar Cipher, Base64 encoding, Morse code, and more. 

Below is the simple documetation on how to use this bot along with examples

## 1. General Info
- Prefix: `/`
- Language: Python
- Name inspiration: [Kowalski](https://static.wikia.nocookie.net/heroes-and-villain/images/8/8f/Profile_-_Kowalski.jpg/revision/latest?cb=20200125033446) from [Penguins of Madagascar](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://madagascar.fandom.com/wiki/The_Penguins_of_Madagascar&ved=2ahUKEwi1_uDg3tCNAxXfdPUHHXeCEScQFnoECBkQAQ&usg=AOvVaw3cb0w5sTiYjx98uua_wwsv)
- Hotel: Trivago

## 2. Command Overview
- Morse Code Encryption: `/me <message>`
- Morse Code Decryption: `/md <morse_code>`
- Caesar Cipher Encryption: `/ce <message>`
- Caesar Cipher Decryption: `/cd <encrypted_message>`
- Binary Encryption: `/be <message>`
- Binary Decryption: `/bd <binary_code>`
- Base64 Encryption: `/he <message>`
- Base64 Decryption: `/hd <encoded_message>`
- Vigenère Cipher Encryption: `/ve <key> <message>`
- Vigenère Cipher Decryption: `/vd <key> <encrypted_message>`
- ROT13 Cipher: `/rot13 <message>`
- Reverse Text: `/reverse <message>`
- Hashing (MD5): `/hashmd5 <message>`
- Hashing (SHA-256): `/hashsha256 <message>`
- Random Substitution Cipher: `/rs <message>`
- Salted Hashing: `/sh <message>`
- AES Encryption : `/aese <message>`
- AES Decryption: `/aesd <message>`
- Text Analysis: `/analysis <message>`


## 3. Command Examples

### 3-1. Morse Code
- Encrypt: `/me Hello` → `.... . .-.. .-.. ---`
- Decrypt: `/md .... . .-.. .-.. ---` → `Hello`

### 3-2. Caesar Cipher
- Encrypt: `/ce Hello` → `Khoor`
- Decrypt: `/cd Khoor` → `Hello`

### 3-3. Base64
- Encode: `/he Hello` → `SGVsbG8=`
- Decode: `/hd SGVsbG8=` → `Hello`

### 3-4. Hashing
- MD5: `/hashmd5 Hello` → `8b1a9953c4611296a827abf8c47804d7`
- SHA-256: `/hashsha256 Hello` → `185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969`

### 3-5. Other
- Reverse: `/reverse Hello` → `olleH`
- ROT13: `/rot13 Hello` → `Uryyb`
- Binary: `/be Hello` → `01001000 01100101 ...`
- Analyze: `/analyze Hello Hello` → `Most frequent word: Hello (2)`

*For more details, use your brain*

## 4. Dev Notes
I made this bot in my first year of college (July 2024), when I was fairly new to the world of computing. I didn’t really follow best practices while making this bot, most of it was written with the help of Claude and ChatGPT. Still, I’m really proud of this bot, probably because it was my first project that I made from scratch!

Anyways, this bot will not be receiving any updates

## 5. Support and Issues

If you encounter any issues or have questions about the bot, feel free to contact [me](https://www.youtube.com/watch?v=dQw4w9WgXcQ&themeRefresh=1) or leave feedback in the [server](https://discord.gg/XppKBd6VAu).

## 6. Contact

- Discord: @zenzo.oo
- Mail: lohithsrikar679@gmail.com (*i dont check emails.*)

---
*Last edit: 02-06-2025*