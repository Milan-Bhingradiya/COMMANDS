# Linux Commands Guide

## System Information
```sh
uname -a        # Display system information
hostname        # Show system hostname
uptime          # Show system uptime
df -h           # Show disk space usage
free -m         # Show memory usage
```

## File and Directory Management
```sh
ls -la          # List files with details
cd /path        # Change directory
pwd             # Show current directory
mkdir newdir    # Create a new directory
rm -r dirname   # Remove directory and contents
```

## File Operations
```sh
touch file.txt        # Create an empty file
cp file1 file2        # Copy file
mv file1 file2        # Move or rename file
rm file.txt           # Remove file
cat file.txt          # View file contents
tail -n 10 file.txt   # Show last 10 lines of file
head -n 10 file.txt   # Show first 10 lines of file
```

## User Management
```sh
whoami         # Show current user
id             # Show user ID
groups        # Show user groups
adduser user  # Create a new user
passwd user   # Change user password
```

## Permissions
```sh
chmod 755 file.txt     # Change permissions
chown user:group file  # Change owner
ls -l file.txt         # Show file permissions
```

## Process Management
```sh
ps aux         # Show running processes
top            # Interactive process viewer
kill PID       # Terminate a process by PID
killall name   # Kill all processes with name
```

## Networking
```sh
ifconfig          # Show network interfaces
ping google.com   # Ping a host
netstat -tulnp    # Show open ports
curl -I example.com # Fetch HTTP headers
```

## Package Management
### Debian-based (Ubuntu, Debian)
```sh
apt update       # Update package list
apt upgrade      # Upgrade installed packages
apt install pkg  # Install package
apt remove pkg   # Remove package
```
### RedHat-based (CentOS, Fedora)
```sh
yum update       # Update packages
yum install pkg  # Install package
yum remove pkg   # Remove package
```

## Searching and Finding Files
```sh
find / -name file.txt  # Find file by name
grep "word" file.txt   # Search for word in file
```

## Disk and Storage
```sh
df -h            # Show disk usage
du -sh folder    # Show folder size
mount /dev/sdb1 /mnt  # Mount drive
umount /mnt      # Unmount drive
```

## Archiving and Compression
```sh
tar -cvf archive.tar folder  # Create tar archive
tar -xvf archive.tar         # Extract tar archive
gzip file.txt                # Compress file
gunzip file.txt.gz           # Decompress file
```

## Shell Scripting
```sh
echo "Hello World"  # Print text
bash script.sh      # Run script
./script.sh         # Execute script (make executable with chmod +x script.sh)
```

## Other Useful Commands
```sh
history          # Show command history
alias ll='ls -la'  # Create alias
clear            # Clear terminal
reboot          # Restart system
shutdown now    # Shutdown system
```

This guide provides a quick reference for essential Linux commands.

