# Linux Basics

## What is Linux?
- Linux is an open-source operating system based on Unix, known for its stability, security, and flexibility. It is widely used for servers, development, and personal computing.
- Developed by Linus Torvalds in 1991.

## How to Install Linux
- **WSL (Windows Subsystem for Linux)**: Runs a Linux distribution within Windows.
- **VirtualBox**: Install Linux as a virtual machine on your existing OS.
- **Vagrant**: Uses automation to set up and manage virtual environments.
- **Bare Metal Install**: Install Linux directly on your system as the primary OS.
- **Cloud Platforms**: Run a Linux instance on AWS, GCP, Azure, etc.

## Difference Between Linux and Windows

| Feature         | Linux                              | Windows                          |
|---------------|--------------------------------|--------------------------------|
| **Source**    | Open-source, freely available | Proprietary, licensed         |
| **Customization** | Highly customizable        | Limited customization options |
| **Security**  | More secure, fewer viruses   | More vulnerable to malware    |
| **User Interface** | CLI & GUI options available | Primarily GUI-based          |
| **Performance** | Efficient, lightweight     | Can be resource-heavy        |
| **Software Compatibility** | Supports open-source apps | Supports commercial software |
| **File System** | Ext4, XFS, Btrfs           | NTFS, FAT32, exFAT          |
| **Usage**      | Servers, development, security | Gaming, business, general use |

## Difference Between Linux and Unix
- **Linux**: Open-source, available in multiple distributions.
- **Unix**: Mostly proprietary, used in enterprise environments.

## Important Linux Components
- **Kernel**: Core of the OS, manages hardware and processes (written in C program to interact with hardware but everyone doesn't know how to navigate with it, hence a shell acts as a wrapper around it for easy interactions using shell commands).
- **Bootloader**: Loads the OS into memory at startup (the primary boot program, or bootloader, is typically GRUB (Grand Unified Bootloader)).
- **Shell**: Command-line interface for interacting with the system.

## Linux System Architecture
![Linux System Architecture](https://github.com/user-attachments/assets/07cf3593-7711-4dfd-bc76-13de3e70ca7d)

### Components:
1. **Hardware** – The physical components like CPU, memory, and storage.
2. **Kernel** – The core of Linux that manages hardware, process scheduling, memory, and system calls.
3. **System Libraries** – Provide essential functions for applications to interact with the kernel.
4. **User Space (Shell & Applications)** – Includes command-line shells to interact with the kernel, GUI interfaces, and user applications.

## States of Processes in Linux
- **Running**: Actively executing.
- **Sleeping**: Waiting for an event.
- **Stopped**: Paused by a signal.
- **Zombie**: Completed execution but not removed from memory.

## Software Remote Location Server Tools
These tools help manage Linux servers remotely:
- **SSH (Secure Shell)**: Secure remote access to Linux machines.
- **VNC (Virtual Network Computing)**: Remote desktop access.
- **RDP (Remote Desktop Protocol)**: Used for GUI-based remote access.

## Information About Hardware in Linux
Linux provides various commands to check hardware details:
- `top` – Displays real-time system information, including CPU and memory usage.
- `df -h` – Shows disk space usage in a human-readable format.
- `free -h` – Displays memory usage (RAM and swap) in a human-readable format.
- `lscpu` – Provides details about the CPU architecture.
- `lsblk` – Lists information about block storage devices (like HDDs and SSDs).
- `lspci` – Displays details about PCI buses and attached devices.

## Linux as a File System
In Linux, everything is treated as a **file**, including hardware devices, processes, and configurations. The Linux file system is structured as a **hierarchical tree** starting from the root directory (`/`).

### Key Features of Linux File System
1. **Single Root Directory (`/`)**
   - All files and directories originate from `/`.
2. **Case-Sensitive**
   - `file.txt` and `File.txt` are treated as different files.
3. **Permissions and Ownership**
   - Every file has **read (r), write (w), and execute (x)** permissions for owner, group, and others.
4. **File Systems Supported**
   - Common Linux file systems:
     - **Ext4** (default in most Linux distros)
     - **XFS** (high-performance journaling FS)
     - **Btrfs** (advanced features like snapshots)
5. **Everything is a File**
   - Devices (`/dev`), configurations (`/etc`), and even processes (`/proc`) are represented as files.

### Important Directories in Linux File System

| Directory | Description |
|-----------|-------------|
| `/` | Root directory (base of file system) |
| `/home` | Stores user-specific files & settings |
| `/etc` | System-wide configuration files |
| `/bin` | Essential system binaries |
| `/var` | Log files & variable data |
| `/boot` | Boot loader and kernel files |
| `/usr` | User applications and libraries |
| `/dev` | Device files (e.g., hard drives, USB) |
| `/mnt` | Mount points for external devices |
| `/tmp` | Temporary files, cleared on reboot |


