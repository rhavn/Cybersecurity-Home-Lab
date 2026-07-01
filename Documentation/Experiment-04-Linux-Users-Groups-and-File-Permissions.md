# Experiment 04 - Linux Users, Groups, and File Permissions

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Learn how Linux manages users, groups, file ownership, and file permissions by creating users and groups, modifying ownership, and controlling access to files.

---

## Environment

| Component | Value |
|-----------|-------|
| Operating System | Ubuntu Server 26.04 LTS |
| Virtualization | Oracle VirtualBox |
| User | rhaven |

---

## User Management

### Commands

```bash
whoami
id
groups
```

### Result

Verified the currently logged-in user and inspected the associated user ID (UID), group ID (GID), and group memberships.

---

### Creating a User

**Command**

```bash
sudo adduser analyst
```

### Result

A new user named **analyst** was successfully created with its own home directory and default user group.

---

### Verifying the User

**Command**

```bash
cat /etc/passwd | grep analyst
```

### Result

Confirmed that the **analyst** user was successfully added to the system.

---

### Switching Users

**Commands**

```bash
su - analyst
whoami
pwd
exit
```

### Result

Successfully switched to the **analyst** account, verified the active user, and returned to the original account.

---

## Group Management

### Creating a Group

**Command**

```bash
sudo groupadd security
```

### Result

Created a new group named **security**.

---

### Adding a User to a Group

**Commands**

```bash
sudo usermod -aG security analyst
groups analyst
```

### Result

Successfully added the **analyst** user to the **security** group and verified the membership.

---

## File Ownership

### Creating a Test File

**Command**

```bash
touch report.txt
```

### Result

Created a file that was initially owned by **rhaven**.

---

### Changing Ownership

**Commands**

```bash
sudo chown analyst report.txt
sudo chgrp security report.txt
```

### Result

Successfully changed the file owner to **analyst** and assigned the **security** group as the file's group owner.

---

## File Permissions

### Commands

```bash
chmod 700 report.txt
chmod 644 report.txt
```

### Result

Modified the file permissions to:

| Permission | Meaning |
|------------|---------|
| 700 | Owner has full access; group and others have no permissions. |
| 644 | Owner has read/write access; group and others have read-only access. |

---

## Troubleshooting

### Issue

Attempting to change the permissions of `report.txt` produced the following error:

```text
chmod: Operation not permitted
```

### Cause

The ownership of `report.txt` had previously been changed to the **analyst** user. Since the current user (**rhaven**) was no longer the file owner, Linux denied permission to modify the file's permissions.

### Resolution

Ownership of the file was restored:

```bash
sudo chown rhaven report.txt
```

The file permissions were then successfully modified using:

```bash
chmod 700 report.txt
chmod 644 report.txt
```

### Lesson

Only the file owner or the root user can modify a file's permissions. File ownership plays a critical role in Linux security.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| user-information.png | Viewing current user information, UID, GID, and group memberships |
| user-creation.png | Creating and verifying a new user |
| group-management.png | Creating a group and adding a user to the group |
| file-permissions.png | Changing ownership and modifying file permissions |

---

## Lessons Learned

- Linux separates users and groups to manage access to system resources.
- Every file has an owner and an associated group.
- File ownership determines who is allowed to modify permissions.
- The `chmod` command changes file permissions using symbolic or numeric notation.
- The `chown` command changes file ownership.
- The `chgrp` command changes a file's group ownership.
- Proper permission management is an essential part of Linux system administration and cybersecurity.

---

## Skills Practiced

- Linux User Management
- Linux Group Management
- User Authentication
- File Ownership
- File Permissions
- Linux Security Fundamentals
- System Administration
- Command Line Interface (CLI)
- Technical Documentation

---

## Next Steps

- Learn advanced file permission concepts.
- Understand the difference between symbolic and numeric permission notation.
- Explore special permissions such as **SUID**, **SGID**, and the **Sticky Bit**.
- Configure SSH authentication using public and private keys.