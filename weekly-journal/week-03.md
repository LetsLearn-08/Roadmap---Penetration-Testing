> 📄 View-only content. Licensed under terms in [LICENSE-NOTES.md](../LICENSE-NOTES.md).

# 🖥️ Terminal Commands notes 🗒 

A handy reference for common terminal commands related to file operations, permissions, and process management.

---

## 📁 File Operations

### Create and View Files

touch filename.txt        # Create an empty file
cat filename.txt          # Display file contents
less filename.txt         # View file with scroll
head filename.txt         # Show first 10 lines
tail filename.txt         # Show last 10 lines

### Edit Files

nano filename.txt         # Edit file using nano editor
vim filename.txt          # Edit file using vim editor

### Copy, Move, Rename, Delete

cp source.txt dest.txt    # Copy file
mv oldname.txt newname.txt # Rename or move file
rm filename.txt           # Delete file
rm -r foldername/         # Delete folder recursively

### Directory Operations

mkdir new_folder          # Create directory
ls                        # List files in current directory
ls -l                     # List with details
ls -a                     # Include hidden files
cd foldername/            # Change directory
pwd                       # Show current directory path

## 🔐 Permissions

### View and Change Permissions

ls -l                     # View file permissions
chmod +x script.sh        # Make file executable
chmod 644 filename.txt    # Set read/write for owner, read for others
chown user:group filename.txt  # Change file owner and group

### Symbolic vs Numeric Modes

chmod u+x filename.txt    # Add execute for user
chmod g-w filename.txt    # Remove write for group
chmod o+r filename.txt    # Add read for others

## ⚙️ Process Management

### View Processes, Kill or Manage Processes


ps                        # List current processes
ps aux                    # Detailed list of all processes
top                       # Live process monitor
htop                      # Enhanced top (if installed)

### Background and Foreground

command &                # Run command in background
jobs                     # List background jobs
fg %1                    # Bring job 1 to foreground
bg %1                    # Resume job 1 in background

## Mastering Kali Linux isn’t just about commands—it’s about understanding the system, thinking like a hacker, and staying curious. These notes are your launchpad.
Keep exploring, keep experimenting, and never stop learning. The terminal is your canvas—paint boldly.
 # STAY TUNED TILL NEXT WEEK..@LetsLearn-08



