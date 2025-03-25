# Linux Commands Cheat Sheet

## File Permission Commands

### 1. `umask`
**Usage:**
```sh
umask
umask 022
```
**Description:**
- Sets default permissions for newly created files and directories.
- Common values: `022` (files: `644`, directories: `755`).

### 2. `ls -l`
**Usage:**
```sh
ls -l
```
**Description:**
- Lists files and directories with their permissions, owners, and groups.

### 3. `chmod`
**Usage:**
```sh
chmod 755 filename
chmod u+x script.sh
chmod -R 644 my_directory
```
**Description:**
- Changes file permissions.
- Numeric mode (`755`, `644`): `r=4, w=2, x=1`.
- Symbolic mode (`u+x`, `g-w`, `o+r`).

### 4. `chown`
**Usage:**
```sh
chown user:group filename
chown -R user:group my_directory
```
**Description:**
- Changes ownership of a file or directory.
- `-R` applies recursively.

### 5. `chgrp`
**Usage:**
```sh
chgrp group_name filename
chgrp -R group_name my_directory
```
**Description:**
- Changes group ownership of a file or directory.

---
## Understanding File Permission Codes

Each file and directory in Linux has permission settings assigned to three categories:
1. **User (u)** – The owner of the file.
2. **Group (g)** – Users in the same group as the file.
3. **Others (o)** – All other users.

### Permission Types:
| Symbol | Numeric Value | Description |
|--------|--------------|-------------|
| `r`    | 4            | Read permission (view file contents) |
| `w`    | 2            | Write permission (modify file contents) |
| `x`    | 1            | Execute permission (run as a program/script) |

### Interpreting `ls -l` Output:
Example:
```sh
-rwxr-xr-- 1 user group 1234 Jan 01 12:34 myfile.sh
```
Breakdown:
- `-` → Regular file (`d` for directory, `l` for symbolic link)
- `rwx` → User (owner) permissions: read (`r`), write (`w`), execute (`x`)
- `r-x` → Group permissions: read (`r`), no write (`-`), execute (`x`)
- `r--` → Others: read (`r`), no write (`-`), no execute (`-`)

### Common Permission Values:
| Numeric Code | Permissions | Meaning |
|-------------|------------|---------|
| `777`       | `rwxrwxrwx` | Everyone can read, write, and execute |
| `755`       | `rwxr-xr-x` | Owner can read, write, execute; others can read and execute |
| `644`       | `rw-r--r--` | Owner can read and write; others can only read |
| `600`       | `rw-------` | Owner can read and write; others have no access |
| `400`       | `r--------` | Owner can only read; others have no access |

---
## Compression Commands

### 1. `zip`, `gzip`, and `gunzip`
**Usage:**
```sh
zip archive.zip file1 file2
unzip archive.zip
gzip file.txt
gunzip file.txt.gz
```
**Description:**
- `zip`: Compress multiple files into a `.zip` archive.
- `unzip`: Extract `.zip` files.
- `gzip`: Compress a single file.
- `gunzip`: Decompress `.gz` files.

### 2. `tar` and `untar`
**Usage:**
```sh
tar -cvf archive.tar file1 file2
tar -xvf archive.tar
tar -czvf archive.tar.gz file1 file2
tar -xzvf archive.tar.gz
```
**Description:**
- `tar -cvf`: Create an archive.
- `tar -xvf`: Extract an archive.
- `tar -czvf`: Compress and archive.
- `tar -xzvf`: Extract a compressed archive.

---
## File Transfer Commands

### 1. `scp` (Secure Copy Protocol)
**Usage:**
```sh
scp file.txt user@remote:/path/to/destination
scp -r my_folder user@remote:/path/to/destination
```
**Description:**
- Securely copies files between local and remote machines.
- `-r` for recursive copy (folders).

### 2. `rsync`
**Usage:**
```sh
rsync -av file.txt user@remote:/path/to/destination
rsync -avz my_folder user@remote:/path/to/destination
```
**Description:**
- Synchronizes files between local and remote locations.
- `-a` (archive mode), `-v` (verbose), `-z` (compress data during transfer).
