

# 📁 Linux Commands Project: System-Level File and Directory Operations

## 📌 Project Overview

This project documents the use of key Linux commands for creating, navigating, and managing directories and files—especially within system directories like `/usr`. It includes permission handling, verification steps, and common errors with their resolutions.

---

## 🧰 1. Root Access & Permissions

### 🔒 Understanding Permission Errors

* Attempting to create folders in `/usr` gave:

  ```
  mkdir: cannot create directory '/usr/photos': Permission denied
  ```
* Lesson:

  * Regular users can’t modify system-level directories.
  * Use `sudo` for admin rights.
  * `cd` is a shell built-in; `sudo cd` doesn’t work.

### ✅ Solution: Directory Creation with `sudo`

```bash
sudo mkdir /usr/photos
```

### 🔍 Verification

```bash
ls -l /usr | grep photos
drwxr-xr-x 2 root root 4096 Mar 15 10:00 photos
```

---

## 📂 2. Directory Navigation

### 📍 `pwd` - Print Working Directory

```bash
pwd
/home/ubuntu
```

### 📁 `cd` - Change Directory

```bash
cd /usr/local
```

> `sudo cd` fails because `cd` is a built-in command.

### 📋 `ls` - List Contents

```bash
ls -l /usr
```

> `-l` shows detailed listing. Verified `/usr/photos` exists.

---

## 📄 3. File Operations

### 📝 `touch` - Create Empty File

```bash
touch notes.txt
ls -l notes.txt
```

```
-rw-r--r-- 1 ubuntu ubuntu 0 Mar 15 10:05 notes.txt
```

### 📁 `cp` - Copy Files/Directories

```bash
cp notes.txt notes_backup.txt
cp -r /home/ubuntu/Documents /backup
```

### 🚚 `mv` - Move/Rename

```bash
mv notes.txt important_notes.txt
sudo mv important_notes.txt /usr/photos/
```

### ✅ Verification

```bash
ls /usr/photos/
important_notes.txt
```

---

## ✅ 4. Side Hustle Task 1: Directory Structure Creation

### 📜 Requirements

1. Create `/usr/photos` with subfolders
2. Show full paths
3. List all directories

### 🛠 Implementation

```bash
sudo mkdir -p /usr/photos/{vacation,family,work}
cd /usr/photos
pwd
ls -1
```

### 🔍 Full Directory Structure

```bash
find /usr/photos -type d
```

```
/usr/photos
/usr/photos/vacation
/usr/photos/family
/usr/photos/work
```

---

## 📘 5. Lessons Learned

### 🛡 1. Permission Management

* Practice in `/home` first
* Use `sudo` for system folders

### ⚠️ 2. Shell Built-ins

* `sudo cd` fails
* Use:

  ```bash
  sudo -i
  cd /usr
  ```

### 🔍 3. Verification Is Key

* Always check results with `ls`, `find`
* Compare before/after states

### 🧪 4. Best Practices

```bash
mkdir -p ~/practice/photos
cp -r ~/practice/photos /tmp/backup
sudo cp -r ~/practice/photos /usr/share
```

---

## 🛠 6. Error Corrections & Improvements

| Mistake                      | Fix                                            |
| ---------------------------- | ---------------------------------------------- |
| Used `sudo cd`               | Used `sudo -i` then `cd`                       |
| Permissions denied in `/usr` | Used `sudo` with commands                      |
| No command verification      | Added `ls`, `find`, `pwd` after each operation |
| Lack of explanation          | Added comments and reasoning for each step     |

---

