---
template-version: 1.0.0
aliases: 
creation date: 2024-12-15 10:55
modification date: Sunday 15th December 2024 10:55:45
tags:
  - tutorial
links: https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup
---

extracted-from::[[partitioning]]

# Linux United Keys Setup

## What

a set that can hold up to 8 or 32 keys.

an header on top of the disk.

> The presence of this header is a major difference between LUKS and [dm-crypt](https://en.wikipedia.org/wiki/Dm-crypt "Dm-crypt"), since the header allows multiple different passphrases to be used, with the ability to change and remove them. If the header is lost or corrupted, the device will no longer be decryptable.[5](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup#cite_note-5)


## How
**multi level crypt**

device block encrypted using master key, then key encrypted with each user key.