# Experiment 08 - Network Reconnaissance with Nmap

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Use Nmap from the Kali Linux virtual machine to discover hosts, identify open ports, detect running services, and perform operating system fingerprinting on the Ubuntu Server within the isolated lab network.

---

## Software Used

- Kali Linux
- Ubuntu Server 26.04 LTS
- Nmap 7.98

---

## Lab Environment

| Machine | IP Address | Role |
|---------|------------|------|
| Kali Linux | 192.168.100.20 | Attacker |
| Ubuntu Server | 192.168.100.10 | Target |

---

## Network Verification

Before performing reconnaissance, connectivity between the two virtual machines was verified.

### Command

```bash
ping -c 4 192.168.100.10
```

### Result

The Ubuntu Server responded successfully with no packet loss, confirming communication over the internal lab network.

---

## Reconnaissance Activities

### Basic Port Scan

**Purpose**

Identify open TCP ports on the target machine.

**Command**

```bash
nmap 192.168.100.10
```

**Result**

Open ports discovered:

| Port | Service |
|------|---------|
| 22/tcp | SSH |
| 80/tcp | HTTP |

---

### Service Version Detection

**Purpose**

Determine the software and versions running on open ports.

**Command**

```bash
sudo nmap -sV 192.168.100.10
```

**Result**

Nmap successfully identified the services running on the Ubuntu Server, including the SSH and HTTP services.

---

### Operating System Detection

**Purpose**

Attempt to identify the operating system using TCP/IP fingerprinting.

**Command**

```bash
sudo nmap -O 192.168.100.10
```

**Result**

The scan confirmed that the target was a Linux-based system.

Although Nmap could not determine the exact operating system version, this is common in virtualized environments where fingerprinting accuracy may be reduced.

---

### Aggressive Scan

**Purpose**

Collect additional information using version detection, operating system detection, default NSE scripts, and traceroute.

**Command**

```bash
sudo nmap -A 192.168.100.10
```

**Result**

The aggressive scan provided detailed information about the target services and confirmed the accessibility of the Ubuntu Server.

---

### Network Discovery

**Purpose**

Identify active hosts within the isolated lab network.

**Command**

```bash
nmap 192.168.100.0/24
```

**Result**

Two active hosts were discovered.

| IP Address | Description |
|------------|-------------|
| 192.168.100.10 | Ubuntu Server |
| 192.168.100.20 | Kali Linux |

The Ubuntu Server exposed SSH and HTTP services, while Kali Linux did not expose any open TCP ports.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| ping-ubuntu.png | Connectivity verification |
| nmap-version.png | Installed Nmap version |
| nmap-basic-scan.png | Basic port scan |
| nmap-service-scan.png | Service version detection |
| nmap-os-detection.png | Operating system detection |
| nmap-aggressive-scan.png | Aggressive scan results |
| nmap-network-scan.png | Network host discovery |

---

## Problems Encountered

No critical issues were encountered during this experiment.

Operating system fingerprinting did not produce an exact match, which is expected when scanning virtual machines due to their generic network characteristics.

---

## Lessons Learned

- Reconnaissance is the first phase of a penetration test.
- Nmap can identify live hosts, open ports, and running services.
- Service version detection provides valuable information for vulnerability assessment.
- Operating system fingerprinting may be less accurate in virtualized environments.
- Systems that do not expose unnecessary services present a smaller attack surface.

---

## Verification

The experiment was considered successful after:

- Network connectivity between Kali Linux and Ubuntu Server was verified.
- Open ports on the Ubuntu Server were successfully identified.
- Running services were detected.
- The target operating system was fingerprinted.
- Both virtual machines were discovered during the network scan.

---

## Skills Practiced

- Network Reconnaissance
- Nmap
- Host Discovery
- Port Scanning
- Service Enumeration
- Operating System Fingerprinting
- Network Analysis
- Linux Networking
- Cybersecurity Documentation