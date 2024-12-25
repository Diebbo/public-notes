---
template-version: 1.0.0
aliases: [ encryption]
creation date: 2024-12-15 11:09
modification date: Sunday 15th December 2024 11:09:55
tags: [tutorial  ]
---

extracted-from::[[partitioning]]

## How to
Let me explain the process of potentially reversing or recovering data from a LUKS-encrypted partition when the original partition structure has been altered.

In your scenario, you've used TestDisk and can see some data after the LUKS partition, which is promising. The challenge of reversing LUKS encryption depends on a few critical factors:

1. LUKS Encryption Mechanism
- LUKS stores its encryption metadata in the first 1MB of the partition
- The master key is encrypted by user-provided passphrases
- Without the passphrase or key file, decryption is computationally infeasible

2. Recovery Possibilities
There are a few potential approaches:

a) Passphrase Recovery
- If you remember any passphrase used during LUKS encryption
- Check for saved key files on other drives or backups
- Use `cryptsetup luksDump` to examine key slots

b) Forensic Data Recovery
```bash
# Examine LUKS header information
sudo cryptsetup luksDump /dev/sda
```

c) Metadata Analysis
- Tools like `photorec` or specialized forensic tools can help
- Look for remnants of partition table in disk sectors
- Attempt to reconstruct filesystem structure

3. Advanced Recovery Techniques
- If partial LUKS header is intact, you might:
  1. Identify the original filesystem type
  2. Use sector-level recovery tools
  3. Attempt to map original partition boundaries

4. Critical Warnings
- Do NOT write anything to the drive
- Work on a copy/clone of the original drive
- Recovery is most successful with minimal additional disk activity

Recommended Tools:
- TestDisk (which you've already used)
- PhotoRec
- ddrescue
- Foremost
- scalpel

Specific Next Steps:
1. Create a complete bit-for-bit clone of the drive
```bash
# Clone the entire drive (be extremely careful)
sudo dd if=/dev/sda of=/path/to/safe/backup/drive.img bs=4M status=progress
```

2. Analyze the cloned image
```bash
# Examine disk sectors
sudo fdisk -l /path/to/drive.img
sudo testdisk /path/to/drive.img
```

Questions for you:
1. Do you have any memory of passphrases used?
2. Was this a recent accidental overwrite?
3. Do you have any backup of the original partition table?

The more details you can provide, the more precise recovery strategy I can recommend.

## Recovering 


1. Unlock the LUKS Encrypted Partition
```bash
# Open the encrypted partition
sudo cryptsetup luksOpen /dev/sda3 recovered_drive

# This will prompt you for the passphrase you remember
# The partition will be mapped to /dev/mapper/recovered_drive
```

2. Mount the Decrypted Partition
```bash
# First, identify the filesystem type (likely ext4)
sudo file -s /dev/mapper/recovered_drive

# Create a mount point
sudo mkdir /mnt/recovered_drive

# Mount the filesystem
sudo mount /dev/mapper/recovered_drive /mnt/recovered_drive
```

3. Backup Strategy for Images and Documents
```bash
# Create a directory for backup
mkdir ~/disk_recovery

# Copy images (common extensions)
find /mnt/recovered_drive -type f \( -name "*.jpg" -o -name "*.png" -o -name "*.jpeg" -o -name "*.gif" -o -name "*.bmp" \) -exec cp -t ~/disk_recovery {} +

# Copy documents
find /mnt/recovered_drive -type f \( -name "*.doc" -o -name "*.docx" -o -name "*.pdf" -o -name "*.txt" -o -name "*.xls" -o -name "*.xlsx" \) -exec cp -t ~/disk_recovery {} +
```

4. Verify Backup
```bash
# Check the number of files copied
ls ~/disk_recovery | wc -l
```

Detailed Explanation of the Process:
- `cryptsetup luksOpen` decrypts the LUKS partition using your passphrase
- The decrypted partition becomes accessible like a normal filesystem
- We use `find` with multiple file extensions to comprehensively search and copy files
- The files are copied to a safe location for further review

Potential Challenges to Watch For:
- Ensure you have enough free space for the backup
- The backup location should be on a different drive
- Some files might have unusual extensions, so manual browsing might be necessary

## Mounting nfts


1. Filesystem Characteristics
- NTFS is Windows' primary filesystem since Windows NT
- It supports larger file sizes and more advanced features compared to FAT
- Linux has partial support through kernel modules and third-party tools

2. Linux NTFS Tools
```bash
# Install NTFS support packages
sudo apt-get install ntfs-3g  # Debian/Ubuntu
sudo dnf install ntfs-3g      # Fedora
```

3. Mounting Strategy
```bash
# Create mount point
sudo mkdir /mnt/ntfs_drive

# Mount NTFS partition with read-only permissions
sudo mount -t ntfs-3g /dev/mapper/recovered_drive /mnt/ntfs_drive -o ro
```

Key Mounting Options:
- `-t ntfs-3g`: Specifies NTFS filesystem type
- `-o ro`: **Read-only mode** (prevents accidental modifications)

4. File Recovery Approach
```bash
# Create recovery directory
mkdir ~/ntfs_recovery

# Copy images (NTFS might have different extensions)
find /mnt/ntfs_drive -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" -o -iname "*.gif" -o -iname "*.bmp" \) -exec cp -t ~/ntfs_recovery {} +

# Copy documents with Windows-common extensions
find /mnt/ntfs_drive -type f \( -iname "*.doc" -o -iname "*.docx" -o -iname "*.pdf" -o -iname "*.txt" -o -iname "*.xls" -o -iname "*.xlsx" \) -exec cp -t ~/ntfs_recovery {} +
```

Detailed Considerations:
- Case-insensitive search with `-iname`
- Preserves file metadata
- Minimizes risk of data corruption

Additional Recovery Tools:
1. TestDisk (which you've already used)
2. PhotoRec
3. foremost

## Partitioning scanning

```bash
# Detailed partition scanning
sudo fdisk -l /dev/sda
sudo parted /dev/sda print
sudo lsblk

# Low-level sector examination
sudo hexdump -C /dev/sda | less
```
