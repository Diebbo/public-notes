---
template-version: 1.0.0
aliases: 
creation date: 2024-12-11 22:34
modification date: Wednesday 11th December 2024 22:34:24
tags:
  - tutorial
links: https://www.wundertech.net/btrfs-vs-ext4-side-by-side-comparison/
---

extracted-from::[[it/nvim/README]]

btrfs:
- **Copy-on-write(CoW)** git for fs
- snapshots
- data integrity
- built-in raid

ext4:
- previous compatibility
- journaling
- large file system support
- **extents**: set of blocks that are contiguous within a file. + performance - fragmentation
