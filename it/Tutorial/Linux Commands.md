---
tags:
  - command
  - linux
creation: 05_01_2024-21:47
resources: "{{links}}"
---
# Linux Commands
## Ez Ones
1. **File and Directory Operations:**
    
	- `ls`: List files and directories.
    - `cd`: Change directory.
    - `pwd`: Print working directory.
    - `cp`: Copy files/directories.
    - `mv`: Move/rename files/directories.
    - `rm`: Remove/delete files or directories.
    - `mkdir`: Create a new directory.
    
1. **File Viewing and Editing:**
    
	- `cat`: Concatenate and display the content of files.
    - `nano` or `vim`: Text editors for file editing.
    - `head` and `tail`: Display the beginning or end of a file.
    - `less` or `more`: View files page by page.

1. **File System Information:**    
    
	- `df`: Display disk space usage.
    - `du`: Display file/directory disk usage.
    - `lsblk`: List information about block devices.

4. **Process Management:**    
    
	- `ps`: Display information about active processes.
    - `top` or `htop`: Display a dynamic view of system processes.
    - `kill`: Terminate processes.
    - `killall`: Kill processes by name.

5. **User Management:**
    
	- `who`: Display information about currently logged in users.
    - `w`: Display information about users and their activities.
    - `useradd`, `userdel`, `usermod`: User management commands.
    - `passwd`: Change user password.

6. **System Information:**

	- `uname`: Display system information.
    - `hostname`: Display or set system hostname.
    - `uptime`: Display how long the system has been running.
    - `free`: Display free and used memory.

7. **Networking:**

    - `ifconfig` or `ip`: Display network interface information.
    - `ping`: Test network connectivity.
    - `traceroute` or `mtr`: Trace the route to a network host.
    - `netstat` or `ss`: Display network connections.

9. **Package Management:**
    
    - `apt` (Debian/Ubuntu) or `yum` (Red Hat/CentOS): Package management commands.
    - `dpkg` (Debian/Ubuntu) or `rpm` (Red Hat/CentOS): Low-level package management.

9. **System Logs:**    

	- `dmesg`: Display kernel ring buffer.
    - `journalctl`: Query and display messages from the journal.
    - `tail` or `less` on log files in `/var/log/`.

10. **Compression and Archiving:**    

    - `tar`: Create, list, extract, or update compressed archive files.
    - `gzip`, `bzip2`, `xz`: Compress or decompress files.

## Arch Based
1. **Pacman Package Management:**
    
    - `pacman`: Package manager for Arch Linux.
    - `yay`: AUR helper for installing packages from the Arch User Repository.

2. **System Management:**
    
    - `systemctl`: Examine and control the systemd system and service manager.
    - `journalctl`: Query and display messages from the journal.

## Little complex
1. **File and Text Processing**
    
    - `cat`: Concatenate and display the content of files.
        
        `cat file.txt`
        
    - `grep`: Search for a specific pattern in files.
        
        `grep "pattern" file.txt`
        
    - `awk`: Process and analyze text data in files.
        
        `awk '{print $1}' file.txt`
        
    - `sed`: Stream editor for filtering and transforming text.
        
        `sed 's/old/new/' file.txt`
        
2. **Archive and Compression**
    
    - `tar`: Create, list, extract, or update compressed archive files.
        
        `tar -cvf archive.tar.gz /path/to/directory`
        
3. **File Transfer**
    
    - `rsync`: Efficiently copy and synchronize files between directories.
        
        `rsync -av source/ destination/`
        
    - `curl`: Transfer data with URLs.
        
        `curl -O https://example.com/file.txt`
        
    - `wget`: Retrieve files from the web using URLs.
        
        `wget https://example.com/file.zip`
        
4. **Disk Usage**
    
    - `ncdu`: Interactive disk usage analyzer with an easy-to-use interface.
        
        `ncdu /path/to/directory`
        
5. **Process Monitoring**
    
    - `htop`: Interactive process viewer and system monitor.
        
        `htop`
        
6. **File Finding**
    
    - `fd`: A faster and user-friendly alternative to `find`.
        
        `fd "pattern" /path/to/search`
        
7. **Command-line Tools**
    
    - `tldr`: Simplified and community-driven man pages.
        
        `tldr command`
        
    - `tree`: Display directory tree structures.
        
        `tree /path/to/directory`
        
    - `fzf`: Command-line fuzzy finder.
        
        `find /path/to/search | fzf`
        
8. **Miscellaneous**
    
    - `exa`: A modern replacement for `ls`.
        
        `exa -l`