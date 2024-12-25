---
template-version: 1.0.0
aliases: 
creation date: 2024-12-11 22:41
modification date: Wednesday 11th December 2024 22:41:15
tags:
  - tutorial
  - fs
link: https://computingforgeeks.com/how-to-resize-xfs-btrfs-file-systems-on-linux/
---

extracted-from::[[it/nvim/README]] [[btrfs-ext4]]

# FS

types: EXT, EXT2, EXT3, EXT4, JFS, Swap, XFS, ReiserFS, Btrfs e.t.c

>[!Info] **Note**
>The **_XFS_** file system is referred to as the high-speed JFS(Journaled File System).


| **File System** | **Utility Tool**          | **Grow**       | **Shrink**    |
| --------------- | ------------------------- | -------------- | ------------- |
| **_XFS_**       | `xfs_growfs`              | Online         | Not supported |
| **_Btrfs_**     | `btrfs filesystem resize` | Online         | Online        |
| **_Ext2_**      | `resize2fs`               | Online/Offline | Offline only  |
| **_Ext3_**      | `resize2fs`               | Online/Offline | Offline only  |
| **_Ext4_**      | `resize2fs`               | Online/Offline | Offline only  |

# Resizing
## Summary of commands
- `lsblk` : List information about block devices.
- `cfdisk`: terminal tool to create partitions
- `sudo mkfs.xfs /dev/sdb<part_num> -f` or `sudo mkfs.btrfs /dev/sdb1 -f`
- `mount`
- `df -h` : disk free
- `sudo xfs_growfs -d <size?> /mount/point` if no size => max
- `sudo btrfs resize <amount> /mnt/path` with amount being f.e.+/-1G or max.