 Linux Commands  

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
