# System-Level Commands

## 1. `uname`
**Description:**
Displays system information, including the OS name, kernel version, and architecture.

**Command:**
```sh
uname (Darwin for MAC, Linux for ubuntu and other Linux distros)
uname -a  # Shows all system information
uname -r  # Displays kernel version
```

## 2. `uptime`
**Description:**
Shows how long the system has been running and the system load.

**Command:**
```sh
uptime
```

## 3. `date`
**Description:**
Displays the current date and time.

**Command:**
```sh
date  # Show current date and time
```

## 4. `who`, `whoami`
**Description:**
- `who`: Shows logged-in users.
- `whoami`: Shows the current user.

**Commands:**
```sh
who  # Lists logged-in users
whoami  # Displays the current user
```

## 5. `which`
**Description:**
Locates the path of an executable command.

**Command:**
```sh
which python  # Shows the path of the python binary
```

## 6. `id`
**Description:**
Displays user and group IDs.

**Command:**
```sh
id  # Show UID and GID
```

## 7. `sudo`
**Description:**
Allows a permitted user to execute a command as the superuser. This itself is a group to which the user gets added if runs sudo command to access high level priveleges.

**Command:**
```sh
sudo command_name  # Run a command as root
sudo apt update  # Updates package lists
sudo apt remove package
```

## 8. `shutdown`
**Description:**
Shuts down or reboots the system.

**Command:**
```sh
sudo shutdown -h now  # Shutdown immediately
sudo shutdown -r now  # Reboot immediately
```

## 9. `reboot`
**Description:**
Reboots the system.

**Command:**
```sh
sudo reboot  # Restart the system
```

## 10. `apt`
**Description:**
Package manager for Debian-based systems (e.g., Ubuntu).

**Command:**
```sh
sudo apt update  # Update package lists
sudo apt install package_name  # Install a package
```

## 11. `yum`
**Description:**
Package manager for RPM-based distributions (e.g., CentOS, RHEL).

**Command:**
```sh
sudo yum update  # Update packages
sudo yum install package_name  # Install a package
```

## 12. `dnf`
**Description:**
Modern replacement for `yum` on Fedora and RHEL.

**Command:**
```sh
sudo dnf install package_name  # Install a package
```

## 13. `pacman`
**Description:**
Package manager for Arch Linux and its derivatives.

**Command:**
```sh
sudo pacman -Syu  # Update system
sudo pacman -S package_name  # Install a package
```

## 14. `portage`
**Description:**
Package management system for Gentoo Linux.

**Command:**
```sh
sudo emerge --sync  # Sync package database
sudo emerge package_name  # Install a package
```
Here’s the revised list with `su` placed appropriately in the **User & Group Management Commands** section:  

---

## **User & Group Management Commands **  

### **15. `su` (Switch User)**  
**Description:**  
The `su` (substitute user) command allows switching to another user account, including root.  
**Examples:**  
```sh
su username  # Switch to another user
su -  # Switch to the root user (if allowed)
```
- If you need root access, you must enter the root password unless using `sudo su`.  
- The `-` option loads the target user’s environment variables and shell profile.  

### **16. `groupadd`**  
**Description:**  
Creates a new group on the system.  
**Example:**  
```sh
sudo groupadd groupname
```

### **17. `groupdel`**  
**Description:**  
Deletes a group from the system.  
**Example:**  
```sh
sudo groupdel groupname
```

### **18. `passwd -a, -m`**  
**Description:**  
- `-a` : Apply password changes to all users.  
- `-m` : Enable a user’s account after being disabled.  
**Example:**  
```sh
sudo passwd -a username  # Change password for all users
sudo passwd -m username  # Unlock a disabled user account
```

---

## **Additional Important System Commands**

### **19. `cat /etc/passwd`**  
**Description:**  
Displays user account details stored in `/etc/passwd`.  
Each line follows the format:  
`username:x:UID:GID:Full Name:Home Directory:Shell`  
**Example:**  
```sh
cat /etc/passwd
```

### **20. `cat /etc/group`**  
**Description:**  
Displays all groups and their members.  
**Example:**  
```sh
cat /etc/group
```

### **21. `cat /etc/shadow`**  
**Description:**  
Contains encrypted passwords of users (only accessible by root).  
**Example:**  
```sh
sudo cat /etc/shadow
```

### **22. `usermod`**  
**Description:**  
Modify user details like home directory, shell, or groups.  
**Example:**  
```sh
sudo usermod -aG sudo username  # Add user to sudo group
sudo usermod -l new_username old_username  # Change username
```

### **23. `last`**  
**Description:**  
Shows the login history of users.  
**Example:**  
```sh
last
```

### **24. `w`**  
**Description:**  
Displays active users and what they are doing.  
**Example:**  
```sh
w
```

### **25. `finger`** *(if installed)*  
**Description:**  
Shows detailed information about a user.  
**Example:**  
```sh
finger username
```

### **26. `deluser`**  
**Description:**  
Removes a user account.  
**Example:**  
```sh
sudo deluser username
```

### **27. `delgroup`**  
**Description:**  
Removes a group from the system.  
**Example:**  
```sh
sudo delgroup groupname
```


