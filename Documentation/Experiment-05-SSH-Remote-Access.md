# Experiment 05 - SSH Remote Access

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Configure and verify secure remote access to the Ubuntu Server using the Secure Shell (SSH) protocol from the Windows host machine.

---

## Environment

| Component | Value |
|-----------|-------|
| Operating System | Ubuntu Server 26.04 LTS |
| Virtualization | Oracle VirtualBox |
| Network Mode | NAT with Port Forwarding |
| SSH Server | OpenSSH Server |
| Host Operating System | Windows 10 |

---

## Verifying the SSH Service

### Command

```bash
sudo systemctl status ssh
```

### Purpose

Checks whether the OpenSSH service is installed and currently running.

### Result

The SSH service was active and running, allowing the server to accept remote SSH connections.

---

## Verifying the Server IP Address

### Command

```bash
ip addr
```

### Purpose

Displays the network interfaces and assigned IP addresses.

### Result

The server received the IPv4 address:

```text
10.0.2.15
```

This address was assigned by the VirtualBox NAT network.

---

## VirtualBox Port Forwarding

### Configuration

To allow the Windows host to connect to the Ubuntu Server through NAT, a port forwarding rule was created.

| Setting | Value |
|---------|-------|
| Protocol | TCP |
| Host Port | 2222 |
| Guest Port | 22 |

### Why?

VirtualBox NAT does not allow inbound connections by default. Port forwarding maps a port on the host computer to the SSH service running inside the virtual machine.

---

## Connecting via SSH

### Command (Windows PowerShell)

```powershell
ssh rhaven@localhost -p 2222
```

### First Connection

On the first connection, SSH displayed the server's fingerprint:

```text
The authenticity of host 'localhost' can't be established...
```

After verifying the connection, the fingerprint was accepted by typing:

```text
yes
```

The server's public key was then stored in the Windows known_hosts file.

---

## Successful Remote Login

After entering the user password, the SSH session was successfully established.

### Verification Commands

```bash
whoami
hostname
pwd
```

### Results

| Command | Result |
|----------|--------|
| `whoami` | rhaven |
| `hostname` | rhaven |
| `pwd` | /home/rhaven |

These commands confirmed that the remote session was successfully connected to the Ubuntu Server.

---

## How SSH Works

SSH (Secure Shell) is a network protocol that allows secure remote administration of Linux systems using encrypted communication.

During the connection process:

1. The SSH client contacts the SSH server.
2. The server presents its public key.
3. The client verifies and stores the server fingerprint.
4. The user authenticates using a password.
5. An encrypted remote terminal session is established.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| ssh-service-status.png | Verifying that the SSH service is running |
| server-ip.png | Viewing the server's IP address |
| virtualbox-port-forwarding.png | Port forwarding configuration |
| successful-ssh-login.png | Successful remote login from Windows |

---

## Problems Encountered

### Issue

The Windows host could not initially connect to the Ubuntu Server using SSH.

### Cause

VirtualBox NAT networking blocks incoming connections unless a port forwarding rule is configured.

### Resolution

Configured VirtualBox NAT Port Forwarding:

- Host Port: **2222**
- Guest Port: **22**

After applying the rule, SSH connections from the Windows host succeeded.

---

## Lessons Learned

- SSH provides secure remote access to Linux systems.
- The SSH service must be running before remote connections are possible.
- VirtualBox NAT requires port forwarding for inbound connections.
- The first SSH connection requires verification of the server fingerprint.
- SSH encrypts communication between the client and server.

---

## Skills Practiced

- SSH
- OpenSSH
- Linux Services
- Remote Administration
- VirtualBox Networking
- NAT
- Port Forwarding
- Windows PowerShell
- Linux Command Line
- Technical Documentation

---

## Next Steps

- Configure SSH key-based authentication.
- Disable password authentication.
- Secure the SSH configuration file.
- Connect to the Ubuntu Server from a Kali Linux virtual machine.