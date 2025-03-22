 ## 1. `ls` - List Directory Contents  
Lists files and directories in the current location.  

### Common Variants:  
- `ls` - Lists files and directories (excluding hidden ones).  
- `ls -a` - Shows all files, including hidden ones (`.` and `..`).  
- `ls -l` - Displays detailed information (permissions, owner, size, etc.).  
- `ls -lh` - Human-readable file sizes in long format.  
- `ls -lt` - Sorts files by modification time.  

## 2. `cd` - Change Directory  
Navigates between directories.  

### Common Variants:  
- `cd /path/to/directory` - Moves to a specific directory.  
- `cd ..` - Moves up one level.  
- `cd ~` - Moves to the home directory.  
- `cd -` - Moves to the last visited directory.  

## 3. `pwd` - Print Working Directory  
Displays the full path of the current directory.  

## 4. `mkdir` - Create Directories  
Creates new directories.  

### Common Variants:  
- `mkdir newdir` - Creates a single directory.  
- `mkdir -p parent/child` - Creates nested directories.  

## 5. Delete Directory/Files (`rm`, `rmdir`)  
Deletes files or directories.  

### Common Variants:  
- `rm filename` - Deletes a file.  
- `rm -r directory` - Deletes a directory and its contents.  
- `rm -f filename` - Forces deletion without confirmation.  
- `rmdir directory` - Removes an empty directory.  

## 6. `cat`, `zcat` - View File Contents  
Concatenates and displays file contents.  

### Common Variants:  
- `cat filename` - Displays file content.  
- `cat file1 file2 > combined.txt` - Merges files into one.  
- `zcat file.gz` - Views compressed `.gz` files without extraction.  

## 7. `touch` - Create Empty Files  
Creates an empty file or updates timestamp.  

### Common Variants:  
- `touch filename` - Creates an empty file.  
- `touch -t YYYYMMDDhhmm filename` - Changes file timestamp.  

## 8. `head` - View First Lines of a File  
Displays the first 5 lines of a file by default.  

### Common Variants:  
- `head -n 20 filename` - Shows the first 20 lines.  

## 9. `tail`, `tail -f` - View Last Lines of a File  
Displays the last lines of a file.  

### Common Variants:  
- `tail -n 20 filename` - Shows the last 20 lines.  
- `tail -f logfile` - Continuously updates and displays new lines as they are written.  

## 10. `less`, `more` - Paginate File Contents  
Used for scrolling through file content.  

### Common Variants:  
- `less filename` - Opens file with navigation options (`Up/Down` arrows).  
- `more filename` - Similar to `less`, but only allows forward navigation.  

## 11. `cp` - Copy Files and Directories  
Copies files from one location to another.  

### Common Variants:  
- `cp source destination` - Copies a file.  
- `cp -r sourcedir destdir` - Copies a directory recursively.  

## 12. `mv` - Move/Rename Files  
Moves or renames files and directories.  

### Common Variants:  
- `mv oldname newname` - Renames a file.  
- `mv file /new/path/` - Moves a file to a new location. 

## 13. `echo` - Print Text to Terminal  
Displays a line of text or variables.  

### Common Variants:  
- `echo "Hello, World!"` - Prints text to the terminal.  
- `echo $USER` - Displays the current username.  
- `echo "Text" > file.txt` - Writes text to a file (overwrites existing content).  
- `echo "More text" >> file.txt` - Appends text to an existing file.  
- `echo -e "Line1\nLine2"` - Enables interpretation of escape sequences (e.g., new lines).  

## 14. `wc` - Word Count  
Counts lines, words, and characters in a file.  

### Common Variants:  
- `wc filename` - Shows line, word, and byte count.  
- `wc -l filename` - Shows line count.  
- `wc -w filename` - Shows word count.  
- `wc -c filename` - Shows byte count.  

## 15. `vi` - Text Editor  
A powerful text editor in Linux.  

### Common Commands in `vi`:  
- `i` - Insert mode.  
- `Esc + :w` - Save changes.  
- `Esc + :q` - Quit.  
- `Esc + :wq` - Save and quit.  

## 16. `ln` - Create Links (Hard & Soft)  
## Hard Link  

A **hard link** is another reference (alias) to a file that shares the same inode and data blocks as the original file.  

### **Syntax:**  
```bash
ln original_file hard_link


echo "Hello World" > file.txt
ln file.txt file_hardlink
ls -li file.txt file_hardlink

```
Creates links between files.  

### Key Features:
- Hard links point to the same inode as the original file.
- Even if the original file is deleted, the hard link still retains the data.
- Hard links cannot span across different filesystems.
- Hard links cannot be created for directories.

##  Soft Link (Symbolic Link)
A **soft link** (symbolic link) is a shortcut to another file’s path rather than its actual data.

### **Syntax:**  
```bash
ln -s original_file soft_link
```
### Key Features:
- Soft links store the file path, not the actual data.
- If the original file is deleted, the soft link breaks (becomes invalid).
- Soft links can span across different filesystems.
- Soft links can be created for both files and directories.

  ### **Difference Between Hard and Soft Links**  

| Feature              | Hard Link                     | Soft Link (Symbolic Link)  |
|----------------------|-----------------------------|---------------------------|
| **Points To**        | Same inode as the original file | File path of the original file |
| **Inode Number**     | Same as the original file   | Different from the original file |
| **File System**      | Must be on the same filesystem | Can span across different filesystems |
| **Works on Directories** | ❌ No                      | ✅ Yes |
| **Effect of Deleting Original** | File remains intact | Link breaks (becomes invalid) |

> **💡 Aside: What is an Inode?**  
> An **inode** (Index Node) is a data structure in a filesystem that stores metadata about a file, such as permissions, owner, size, and pointers to data blocks.  
> Each file has a unique inode number, but hard links share the same inode, whereas soft links have a different inode.

## 17. `cut` - Extract Sections of a File  
Extracts columns from text files.  

### Common Variants:  
- `cut -d ',' -f2 filename` - Extracts the second column using `,` as a delimiter.  
- `cut -c1-5 filename` - Extracts first five characters.
-  `cut -b 1-4 filename` Extracts first 4 bytes from the file.

## 18. `tee` - Output to File and Terminal  
Writes output to both standard output and a file.  

### Example Usage:  
- `echo "Hello" | tee file.txt` - Prints "Hello" to the terminal and file.txt.  

## 19. `sort` - Sort Lines in a File  
Sorts text files in ascending order by default.  

### Common Variants:  
- `sort filename` - Sorts alphabetically.  
- `sort -r filename` - Sorts in reverse order.  
- `sort -n filename` - Sorts numerically.  

## 20. `clear` - Clear Terminal  
Clears the screen of the terminal.  

## 21. `diff` - Compare Two Files  
Shows differences between two files line by line.  

### Example Usage:  
- `diff file1 file2` - Displays differences.  
- `diff -y file1 file2` - Shows side-by-side comparison.  
- `diff -u file1 file2` - Displays unified format differences.  

## 22. SSH (Secure Shell)
**Command:** `ssh user@hostname`  
- Used for securely connecting to a remote machine.  
- Example: `ssh sona@192.168.1.10`  

## 23. df (Disk Free)
**Command:** `df -h`  
- Displays available and used disk space in a human-readable format.  
- Example: `df -h /home`  

## 24. du (Disk Usage)
**Command:** `du -sh directory_name`  
- Shows the size of a directory or file.  
- Example: `du -sh /var/log`  

## 25. ps (Process Status)
**Command:** `ps aux`  
- Lists currently running processes along with their details.  
- Example: `ps aux | grep firefox`  

## 26. top (Task Manager)
**Command:** `top`  
- Displays real-time system resource usage, including CPU and memory.  
- Press `q` to exit.  

## 27. fuser (Identify Processes Using Files)
**Command:** `fuser filename`  
- Identifies processes that are using a particular file or directory.  
- Example: `fuser /var/log/syslog`  

## 28. kill (Terminate a Process)
**Command:** `kill PID`  
- Sends a signal to terminate a process using its process ID (PID).  
- Example: `kill 1234`  

## 29. nohup (Run Command in Background)
**Command:** `nohup command &`  
- Allows a process to continue running after logging out.  
- Example: `nohup python script.py &`  
  
OR

**Command:** ```nohup your_command >> output.log &```
 - nohup ensures the command keeps running even after logout.
 - ">>" appends the output to output.log instead of overwriting it.
 - & runs the command in the background.

## 30. free (Memory Usage)
**Command:** `free -h`  
- Displays system memory usage in a human-readable format.  

## 31. vmstat (System Performance)
**Command:** `vmstat`  
- Provides information about system performance, including CPU, memory, and disk I/O.  

