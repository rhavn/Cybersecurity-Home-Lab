# Experiment 07 - Kali Linux Installation and Lab Network Configuration

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Install Kali Linux in Oracle VirtualBox and configure a private internal network between the Kali Linux and Ubuntu Server virtual machines.

---

## Software Used

- Oracle VirtualBox
- Kali Linux (Latest Installer ISO)

---

## Virtual Machine Configuration

| Setting | Value |
|---------|-------|
| RAM | 4 GB |
| CPU | 2 Cores |
| Disk | 30 GB |
| Adapter 1 | NAT |
| Adapter 2 | Internal Network (`intnet`) |

---

## Installation Summary

Kali Linux was installed using the default graphical installer.

The following configuration choices were made:

- Selected the default installation options.
- Configured the virtual disk using guided partitioning.
- Used a single partition for the operating system.
- Installed the GRUB bootloader on the virtual disk.
- Completed the installation successfully and logged into the system.

---

## Network Configuration

A dual-network configuration was implemented to support both internet access and communication with the Ubuntu Server virtual machine.

| Interface | Purpose | Configuration |
|-----------|---------|---------------|
| Adapter 1 | Internet Access | NAT (DHCP) |
| Adapter 2 | Lab Network | Internal Network (`intnet`) |

### Static IP Configuration

| Virtual Machine | Interface | IP Address |
|-----------------|-----------|------------|
| Ubuntu Server | enp0s8 | 192.168.100.10/24 |
| Kali Linux | eth1 | 192.168.100.20/24 |

### Why This Configuration?

Using two network adapters separates internet connectivity from the isolated lab environment.

- The NAT adapter provides internet access for downloading software and updates.
- The Internal Network adapter allows secure communication between virtual machines without exposing the lab to the host network.

This setup closely resembles small enterprise network environments and provides a safe platform for future penetration testing exercises.

---

## Connectivity Verification

The network configuration was verified by performing the following tests:

- Successfully pinged Ubuntu Server from Kali Linux.
- Successfully pinged Kali Linux from Ubuntu Server.
- Successfully established an SSH connection from Kali Linux to Ubuntu Server.

These tests confirmed that both virtual machines could communicate over the isolated lab network.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| kali-vm-settings-1.png | Kali virtual machine configuration |
| kali-vm-settings-2.png | NAT network adapter configuration |
| kali-vm-settings-3.png | Internal Network (`intnet`) configuration |
| kali-installation-complete.png | Successful Kali Linux installation |
| kali-ip-address.png | Kali network configuration |
| ubuntu-ip-address.png | Ubuntu network configuration |
| kali-ping-ubuntu.png | Successful connectivity test |
| ubuntu-ping-kali.png | Successful connectivity test |
| kali-ssh-ubuntu.png | SSH connection from Kali to Ubuntu |

---

## Problems Encountered

During the initial network configuration, Kali Linux was unable to communicate with the Ubuntu Server over the Internal Network.

### Cause

The Internal Network interface was initially configured incorrectly, resulting in routing conflicts and an incorrect interface configuration.

### Resolution

The issue was resolved by:

- Reconfiguring the network interfaces.
- Assigning a static IP address to the Internal Network interface.
- Verifying the routing table.
- Testing connectivity using `ping`.
- Confirming successful SSH communication between both virtual machines.

---

## Lessons Learned

- Virtual machines can use multiple network adapters simultaneously for different purposes.
- Static IP addressing simplifies communication inside isolated lab environments.
- Correct routing and interface configuration are essential for successful network communication.
- Network troubleshooting often involves verifying interface status, IP addressing, routing tables, and connectivity.

---

## Verification

The experiment was considered successful after:

- Kali Linux booted successfully.
- Both virtual machines obtained internet connectivity through NAT.
- Static IP addresses were configured successfully.
- Both virtual machines communicated over the Internal Network.
- SSH access from Kali Linux to Ubuntu Server was verified.

---

## Skills Practiced

- Virtualization
- Kali Linux Installation
- Ubuntu Server Administration
- VirtualBox Networking
- NAT Networking
- Internal Networking
- Static IP Configuration
- SSH
- Network Troubleshooting
- Linux Command Line