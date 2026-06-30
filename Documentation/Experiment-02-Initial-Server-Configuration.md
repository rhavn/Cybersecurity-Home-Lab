# Experiment 02 - Initial Server Configuration

**Date:** June 30, 2026

**Status:** ✅ Completed

---

## Objective

Verify the Ubuntu Server installation and become familiar with the Linux command-line environment by exploring basic Linux commands, checking network connectivity, updating the system, and verifying system information.

---

## Basic Linux Commands

### `whoami`

**Purpose**

Displays the currently logged-in user.

**Result**

```text
rhaven
```

---

### `pwd`

**Purpose**

Displays the current working directory.

**Result**

```text
/home/rhaven
```

---

### `ls`

**Purpose**

Lists visible files and directories.

**Result**

No visible files or directories were present in the home directory.

---

### `ls -la`

**Purpose**

Lists all files, including hidden files, with detailed information.

**Observations**

The home directory contained the following default hidden files and directories:

- `.bashrc`
- `.profile`
- `.bash_logout`
- `.cache`
- `.ssh`

These files are used to configure the shell environment and support secure remote access.

---

## Network Verification

### `ip addr`

**Purpose**

Displays all network interfaces and assigned IP addresses.

**Result**

The server received the IPv4 address **10.0.2.15/24** on the `enp0s3` network interface.

---

### `ip route`

**Purpose**

Displays the system routing table.

**Result**

The default gateway was configured as **10.0.2.2**, allowing outbound traffic through VirtualBox NAT.

---

### `ping -c 4 google.com`

**Purpose**

Tests internet connectivity and DNS resolution.

**Result**

- Successfully resolved `google.com`
- 4 packets transmitted
- 4 packets received
- 0% packet loss

This confirmed that the server had internet connectivity and functioning DNS.

---

## System Update

### Commands

```bash
sudo apt update
sudo apt upgrade -y
```

### Result

The package lists were refreshed successfully, and all available system updates were installed.

---

## Troubleshooting

### Issue

The initial `sudo apt update` command returned HTTP 404 errors while downloading package indexes.

### Cause

The selected Ubuntu mirror was temporarily synchronizing with the upstream repositories, making some package indexes temporarily unavailable.

### Resolution

After waiting briefly and running `sudo apt update` again, the package lists downloaded successfully without requiring any configuration changes.

---

## System Information

### Commands

```bash
uname -r
hostnamectl
```

### Results

| Property | Value |
|----------|-------|
| Hostname | rhaven |
| Operating System | Ubuntu 26.04 LTS |
| Kernel | Linux 7.0.0-27-generic |
| Architecture | x86-64 |
| Virtualization | Oracle VirtualBox |

### Why This Matters

Verifying the system information establishes a baseline for future experiments and confirms that the virtual machine is running the expected operating system, kernel version, and virtualization platform.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| basic-linux-commands.png | Basic Linux command execution |
| network-verification.png | Network configuration and connectivity |
| system-information.png | System and kernel information |

---

## Lessons Learned

- Linux uses a hierarchical filesystem with each user having a dedicated home directory.
- Hidden files beginning with a period (`.`) contain user and shell configuration settings.
- The `ip` command provides detailed information about network interfaces and routing.
- NAT networking allows a virtual machine to access the internet through the host computer.
- The `apt` package manager is used to update and maintain Ubuntu systems.
- Repository mirrors can occasionally become unavailable while synchronizing, causing temporary package update failures.

---

## Skills Practiced

- Linux Command Line
- Linux File System Navigation
- Ubuntu Server Administration
- Network Configuration
- IP Address Verification
- Routing Table Analysis
- Internet Connectivity Testing
- Package Management (APT)
- System Verification
- Technical Documentation