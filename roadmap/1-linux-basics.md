ITS JUST AN OVERVIEW OF THE LINUX BASICS-- 
 FOR DETAILED NOTES, SYNTAX and EXAMPLES @ CHECK MY WEEKLY PROGRESS
# Linux Basics 🐧

## Introduction
Linux is an open-source operating system widely used in cybersecurity and pentesting. Popular distros include Kali Linux, Parrot OS, and Ubuntu.

## File System Structure
- `/` — root directory  
- `/etc` — config files  
- `/home` — user directories  
- `/var` — logs and variable files

## Basic Commands
- Navigation: `ls`, `cd`, `pwd`  
- File operations: `cp`, `mv`, `rm`, `mkdir`  
- Viewing files: `cat`, `less`, `head`, `tail`  

## File Permissions
- `chmod`, `chown`  
- Permissions: read (r), write (w), execute (x)  
- Example: `chmod 755 script.sh`

## Users & Groups
- `whoami`, `su`, `sudo`  
- Adding users/groups (basic commands)

## Networking Commands
- `ifconfig` or `ip a`  
- `netstat`, `ss`  
- `ping`, `traceroute`  

## Package Management (Debian/Ubuntu)
- `apt update`, `apt install <package>`

## Basic Shell Scripting
- Variables, loops, conditionals  
- Making script executable: `chmod +x script.sh`

## Useful Tips
- Use `grep` to find text  
- Redirect output with `>` and pipes `|`  
- Use `tail -f /var/log/syslog` to watch logs live

Lets meet at the next topic OS FUNDAMENTALS
