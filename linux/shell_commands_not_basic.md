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

