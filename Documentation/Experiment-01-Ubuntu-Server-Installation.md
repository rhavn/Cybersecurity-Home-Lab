# Experiment 01 - Ubuntu Server Installation

**Date:** June 29, 2026

**Status:** ✅ Completed

## Objective

Install Ubuntu Server in Oracle VirtualBox to serve as the primary Linux server in the home lab.

---

## Software Used

- Oracle VirtualBox
- Ubuntu Server 26.04 LTS (ISO)

---

## Virtual Machine Configuration

| Setting | Value |
|---------|-------|
| RAM | 4 GB |
| CPU | 2 Cores |
| Disk | 30 GB |
| Network | NAT |
| File System | ext4 |

---


## Installation Summary

The Ubuntu Server installation was performed using the default guided installer.

The following configuration choices were made:

- Selected English as the installation language.
- Accepted the default keyboard layout.
- Configured networking using NAT.
- Left the proxy configuration empty.
- Used the default Ubuntu archive mirror.
- Installed the system using the guided storage layout.
- Installed the OpenSSH Server package.

---

## Storage Configuration

The Ubuntu Server installer was configured to use the entire 30 GB virtual disk with the default guided storage layout.

| Partition | Purpose |
|-----------|---------|
| BIOS Boot (1 MB) | Stores bootloader information required for booting in BIOS mode |
| ext4 (≈30 GB) | Root filesystem (/) containing the operating system, applications, and user data |

### Why this configuration?

A single ext4 root partition keeps the system simple and easy to manage while learning Linux administration. This layout is suitable for a small virtual machine and allows me to focus on Linux and networking concepts before learning advanced storage management techniques such as LVM.

## OpenSSH Server

The OpenSSH Server package was installed during the Ubuntu Server installation.

### Why?

Installing OpenSSH allows remote administration of the server using encrypted SSH connections. This will enable future experiments where the server is managed remotely from other virtual machines, such as the Kali Linux VM.

## Installation Complete

The Ubuntu Server installation completed successfully without any critical errors.



## Evidence

| Screenshot | Purpose |
|------------|----------|
| vm-settings-1.png         | Virtual machine configuration |
| network-configuration.png | NAT network configuration     |
| storage-config.png        | Guided storage configuration  |
| storage-config-2.png      | Final partition layout        |
| ssh-config.png            | OpenSSH installation          |
| installation-complete.png | Successful installation       |
| first-login.png           | First successful login        |

## Problems Encountered

No critical issues were encountered during the installation process.

Minor decisions included:

- Choosing between LVM and a standard partition layout.
- Deciding whether to install OpenSSH during setup.

These were resolved by selecting a standard ext4 partition layout and enabling OpenSSH for future remote administration.
---

## Lessons Learned

- Ubuntu Server can be installed using a guided storage configuration for quick deployment.
- NAT networking allows the virtual machine to access the internet through the host computer.
- OpenSSH enables secure remote administration of Linux systems.
- Proper documentation helps create a repeatable installation process.


## Verification

The installation was considered successful after:

- The system rebooted successfully.
- The Ubuntu login prompt appeared.
- Login using the created user account succeeded.
- The OpenSSH package was installed.

## Next Steps

- Update the operating system.
- Verify internet connectivity.
- Learn basic Linux commands.
- Configure SSH access.

## Skills Practiced

- Virtualization
- Linux
- Ubuntu Server
- Storage Configuration
- Networking
- SSH
- Git
- GitHub
- Technical Documentation

## Project Repository Management

### GitHub Repository Configuration

Successfully configured Git to use the correct GitHub account for this project.

### Actions Performed
- Connected the local Git repository to the remote GitHub repository.
- Updated the Git authentication credentials to use the correct GitHub account.
- Verified that commits and pushes were successfully uploaded to the intended GitHub repository.

### Repository

GitHub Repository:
https://github.com/rhavn/Cybersecurity-Home-Lab

### Why This Matters

Correct Git configuration ensures that all commits are associated with the appropriate GitHub account, providing an accurate contribution history and maintaining a professional portfolio.

