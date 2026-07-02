# Experiment 09 - Deploying DVWA (Damn Vulnerable Web Application)

**Date:** July 2, 2026

**Status:** ✅ Complete

---

## Objective

Deploy Damn Vulnerable Web Application (DVWA) on the Ubuntu Server to create a controlled environment for practicing web application security testing.

---

## Environment

| Component | Value |
|-----------|-------|
| Attacker Machine | Kali Linux |
| Target Machine | Ubuntu Server 26.04 LTS |
| Web Server | Apache2 |
| Database | MariaDB |
| Web Application | DVWA |

---

## Installation

### Update Package Lists

**Command**

```bash
sudo apt update
sudo apt upgrade -y
```

**Purpose**

Updated the package index and installed the latest security and software updates.

---

### Install Required Packages

**Command**

```bash
sudo apt install php php-mysqli php-gd libapache2-mod-php php-curl php-xml php-mbstring unzip git mariadb-server -y
```

**Purpose**

Installed PHP, required PHP modules, Git, and MariaDB database server.

---

### Download DVWA

**Commands**

```bash
cd /var/www/html
sudo rm index.html
sudo git clone https://github.com/digininja/DVWA.git
```

**Purpose**

Downloaded the latest DVWA source code into Apache's web root.

---

### Configure DVWA

**Commands**

```bash
cd /var/www/html/DVWA

sudo cp config/config.inc.php.dist config/config.inc.php

sudo chmod -R 777 hackable/uploads

sudo chmod -R 777 config
```

**Purpose**

Created the DVWA configuration file and assigned the required permissions for uploads and configuration.

---

### Configure MariaDB

Started the MariaDB shell:

```bash
sudo mysql
```

Executed the following SQL commands:

```sql
CREATE DATABASE dvwa;

CREATE USER 'dvwa'@'localhost' IDENTIFIED BY 'dvwa';

GRANT ALL PRIVILEGES ON dvwa.* TO 'dvwa'@'localhost';

FLUSH PRIVILEGES;

EXIT;
```

**Purpose**

Created the database and database user required by DVWA.

---

### Configure Database Connection

Edited the DVWA configuration file:

```bash
sudo nano /var/www/html/DVWA/config/config.inc.php
```

Configured the database settings:

```php
$_DVWA['db_server'] = '127.0.0.1';
$_DVWA['db_database'] = 'dvwa';
$_DVWA['db_user'] = 'dvwa';
$_DVWA['db_password'] = 'dvwa';
```

---

### Restart Apache

```bash
sudo systemctl restart apache2
```

---

## Verification

From the Kali Linux virtual machine, opened a web browser and navigated to:

```text
http://192.168.100.10/DVWA
```

The DVWA setup page loaded successfully.

Selected **Create / Reset Database**, then logged in using the default credentials:

```text
Username: admin
Password: password
```

The DVWA dashboard loaded successfully, confirming that the web server, PHP, MariaDB, and DVWA were correctly configured.

---

## Results

Successfully deployed DVWA on the Ubuntu Server.

Verified:

- Apache web server operational
- PHP functioning correctly
- MariaDB database connected
- DVWA accessible from Kali Linux
- Database initialized successfully
- Administrator login successful

---

## Lessons Learned

- Learned how PHP applications interact with Apache and MariaDB.
- Configured a web application manually on a Linux server.
- Created and managed a MariaDB database and user.
- Verified web application deployment across a private VirtualBox network.
- Gained experience troubleshooting web application configuration issues.

---

## Screenshots

- package-installation.png
- mariadb-running.png
- dvwa-cloned.png
- database-created.png
- apache-restarted.png
- dvwa-setup-page.png
- database-reset.png
- dvwa-login.png
- dvwa-dashboard.png