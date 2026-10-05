# 🐧 Linux Cheatsheet

Quick reference for commonly used Linux commands and system operations.

## 📁 Navigation

- [Basic Commands](#basic-commands)
- [File & Directory](#file--directory)
- [File Operations](#file-operations)
- [Permissions](#permissions)
- [Processes](#processes)
- [System Information](#system-information)
- [Package Management](#package-management)
- [Networking](#networking)

---

## Basic Commands

### Current directory

```bash
pwd
```

### List files

```bash
ls
```

Detailed:

```bash
ls -la
```

### Change directory

```bash
cd <directory>
```

Go to home:

```bash
cd ~
```

Go to parent directory:

```bash
cd ..
```

### Clear terminal

```bash
clear
```

---

## File & Directory

### Create directory

```bash
mkdir <directory>
```

Create nested directories:

```bash
mkdir -p <path>
```

### Create empty file

```bash
touch <file>
```

### Display file contents

```bash
cat <file>
```

### View file page by page

```bash
less <file>
```

### Search for text

```bash
grep "<text>" <file>
```

---

## File Operations

### Copy

```bash
cp <source> <destination>
```

### Move / Rename

```bash
mv <source> <destination>
```

### Remove file

```bash
rm <file>
```

### Remove directory

```bash
rm -r <directory>
```

Force remove:

```bash
rm -rf <directory>
```

> ⚠️ Be careful with `rm -rf`. Deleted files are generally not moved to a recycle bin.

---

## Permissions

### View permissions

```bash
ls -l
```

Example:

```text
-rwxr-xr--
```

### Change permissions

```bash
chmod <permission> <file>
```

Example:

```bash
chmod +x script.sh
```

### Change owner

```bash
chown <user>:<group> <file>
```

### Run command as administrator

```bash
sudo <command>
```

---

## Processes

### View running processes

```bash
ps
```

More detailed:

```bash
ps aux
```

### Interactive process monitor

```bash
top
```

### Find a process

```bash
pgrep <process>
```

### Terminate a process

```bash
kill <PID>
```

Force:

```bash
kill -9 <PID>
```

---

## System Information

### Kernel information

```bash
uname -a
```

### Memory usage

```bash
free -h
```

### Disk usage

```bash
df -h
```

### Directory size

```bash
du -sh <directory>
```

### CPU information

```bash
lscpu
```

---

## Package Management

For Ubuntu/Debian:

### Update package information

```bash
sudo apt update
```

### Upgrade packages

```bash
sudo apt upgrade
```

### Install package

```bash
sudo apt install <package>
```

### Remove package

```bash
sudo apt remove <package>
```

### Search package

```bash
apt search <package>
```

---

## Networking

### Show IP information

```bash
ip addr
```

### Test connectivity

```bash
ping <host>
```

### Test HTTP request

```bash
curl <url>
```

### Show listening ports

```bash
ss -tuln
```

### DNS lookup

```bash
nslookup <domain>
```

---

## Useful Commands

| Command    | Purpose                          |
| ---------- | -------------------------------- |
| `pwd`      | Show current directory           |
| `ls -la`   | List files with details          |
| `cd`       | Change directory                 |
| `cp`       | Copy files                       |
| `mv`       | Move / rename files              |
| `rm`       | Remove files                     |
| `grep`     | Search text                      |
| `chmod`    | Change permissions               |
| `chown`    | Change ownership                 |
| `ps`       | View processes                   |
| `top`      | Monitor processes                |
| `free -h`  | Check memory                     |
| `df -h`    | Check disk                       |
| `ip addr`  | Show network interfaces          |
| `ss -tuln` | Show listening ports             |
| `curl`     | Make HTTP requests               |
| `sudo`     | Execute with elevated privileges |
