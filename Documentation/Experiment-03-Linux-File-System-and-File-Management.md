# Experiment 03 - Linux File System and File Management

**Date:** July 1, 2026

**Status:** ✅ Completed

---

## Objective

Learn how to navigate the Linux filesystem and perform common file management tasks using the command line.

---

## Environment

| Component | Value |
|-----------|-------|
| Operating System | Ubuntu Server 26.04 LTS |
| Virtualization | Oracle VirtualBox |
| User | rhaven |

---

## Filesystem Navigation

### Commands

```bash
pwd
cd /
ls
```

### Result

Successfully navigated the Linux filesystem and explored the root directory.

Common directories observed included:

- `/home`
- `/etc`
- `/usr`
- `/var`
- `/tmp`
- `/root`

These directories form the standard Linux filesystem hierarchy.

---

## Directory Management

### Commands

```bash
mkdir filesystem-lab
cd filesystem-lab

mkdir Documents
mkdir Downloads
mkdir Notes
```

### Result

Created a workspace and organized it using multiple directories.

---

## File Management

### Commands

```bash
touch notes.txt
touch todo.txt
touch passwords.txt

echo "I'm using Linux!" > notes.txt

cat notes.txt
```

### Result

Created several text files, wrote data into a file, and displayed its contents.

---

## Copying, Moving, and Renaming Files

### Commands

```bash
cp notes.txt Documents/

mv todo.txt Notes/

mv passwords.txt credentials.txt
```

### Result

Successfully copied, moved, and renamed files using standard Linux commands.

---

## Searching and Deleting Files

### Commands

```bash
find . -name "*.txt"

rm credentials.txt

rmdir Downloads
```

### Result

Located text files within the directory structure and removed unnecessary files and empty directories.

---

## Evidence

| Screenshot | Purpose |
|------------|---------|
| filesystem-navigation.png | Exploring the Linux filesystem |
| directory-creation.png | Creating directories |
| file-management.png | Creating, copying, moving, and renaming files |
| search-and-delete.png | Searching for and deleting files |

---

## Lessons Learned

- Linux organizes files using a hierarchical directory structure.
- Commands such as `mkdir`, `touch`, `cp`, `mv`, and `rm` provide efficient file management.
- The `find` command is useful for locating files within a directory tree.
- Care should be taken when deleting files because the `rm` command permanently removes data.

---

## Skills Practiced

- Linux Command Line
- Linux File System Navigation
- Directory Management
- File Creation
- File Copying
- File Movement
- File Renaming
- File Searching
- File Deletion
- Technical Documentation