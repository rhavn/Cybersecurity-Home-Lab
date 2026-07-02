# Experiment 06 - Apache Web Server Deployment

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Install, configure, and verify the Apache HTTP Server on Ubuntu Server to host a simple web page and understand basic web server administration.

---

## Environment

| Component | Value |
|-----------|-------|
| Operating System | Ubuntu Server 26.04 LTS |
| Virtualization | Oracle VirtualBox |
| Web Server | Apache2 |
| Network Mode | NAT with Port Forwarding |

---

## Installing Apache

### Commands

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install apache2 -y
```

### Purpose

Updated the package repository, upgraded installed packages, and installed the Apache HTTP Server.

### Result

Apache2 was successfully installed along with its required dependencies.

---

## Verifying the Apache Service

### Commands

```bash
sudo systemctl status apache2
sudo systemctl is-enabled apache2
```

### Purpose

Verified that the Apache service was running and configured to start automatically during system boot.

### Result

The Apache service was active (`running`) and enabled for automatic startup.

---

## Configuring VirtualBox Port Forwarding

### Configuration

To allow the Windows host machine to access the web server running inside the virtual machine, a VirtualBox NAT port forwarding rule was configured.

| Setting | Value |
|---------|-------|
| Protocol | TCP |
| Host Port | 8080 |
| Guest Port | 80 |

### Why?

VirtualBox NAT blocks inbound connections by default. Port forwarding maps the host's port **8080** to the guest's HTTP service running on port **80**.

---

## Accessing the Apache Web Server

### URL

```text
http://localhost:8080
```

### Result

The Apache2 default welcome page loaded successfully, confirming that the web server was functioning correctly.

---

## Creating a Custom Web Page

### Commands

```bash
cd /var/www/html
ls
sudo mv index.html index.html.bak
sudo nano index.html
```

### Purpose

The default Apache web page was backed up and replaced with a custom HTML page created for the home lab.

### Custom HTML

The custom page displayed:

- Cybersecurity Home Lab
- Author name
- Experiment information
- Running services

### Result

Refreshing the browser displayed the newly created web page, confirming that Apache was serving custom web content.

---

## Verifying the Web Server

### Command

```bash
curl localhost
```

### Purpose

Verified that Apache served the custom HTML page locally from the Ubuntu Server.

### Result

The HTML source of the custom web page was displayed in the terminal, confirming successful web server operation.

---

## How Apache Works

Apache is an open-source HTTP web server that listens for incoming HTTP requests on port **80** and responds by serving web content stored in the document root.

By default, Apache stores website files in:

```text
/var/www/html
```

When a browser requests a page, Apache locates the requested file and returns it to the client over HTTP.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| apache-service-status.png | Apache service running |
| http-port-forwarding.png | VirtualBox HTTP port forwarding configuration |
| apache-default-page.png | Default Apache welcome page |
| custom-webpage.png | Custom HTML page displayed |
| curl-localhost.png | Verifying Apache using curl |

---

## Problems Encountered

No critical issues were encountered during the installation and configuration.

Minor configuration included:

- Creating a VirtualBox NAT port forwarding rule.
- Replacing the default Apache web page with a custom HTML page.

---

## Lessons Learned

- Apache can be installed using the Ubuntu package manager.
- The `systemctl` command is used to manage Linux services.
- VirtualBox NAT requires port forwarding for web services to be accessible from the host.
- Apache serves web pages from the `/var/www/html` directory by default.
- The `curl` utility provides a quick method for verifying web server responses from the command line.

---

## Skills Practiced

- Linux Package Management
- Apache HTTP Server
- Web Server Administration
- Linux Services
- Systemctl
- VirtualBox Networking
- NAT Port Forwarding
- HTTP
- HTML
- Technical Documentation

---

## Verification

The deployment was considered successful after:

- Apache installed successfully.
- The Apache service was active and enabled.
- The default Apache web page was accessible from the Windows host.
- A custom HTML page replaced the default page.
- `curl localhost` returned the custom HTML content.

---

## Next Steps

- Install Kali Linux.
- Configure host-only networking between virtual machines.
- Deploy a vulnerable web application (DVWA).
- Perform basic web security testing using Kali Linux.