# Linux Terminal Commands – File & Directory Management

## Overview

Linux systems are commonly interacted with through a **command-line interface (CLI)** using a shell such as **bash**.

The terminal allows you to:
- Navigate directories
- Create and remove files
- Move and copy files
- Inspect file contents
- Manage permissions

Understanding these commands is essential for working with:
- remote servers
- development environments
- Git repositories
- containerized systems (Docker)

---

# Directory Navigation

## Print Current Directory

```bash
pwd
```

**Meaning:** *Print Working Directory*

Displays the absolute path of the current directory.

Example output:

```
/home/user/projects/my-app
```

---

## List Directory Contents

```bash
ls
```

Lists files and folders in the current directory.

Useful variations:

```bash
ls -l
```

Shows detailed information (permissions, owner, size).

```bash
ls -a
```

Shows hidden files (files starting with `.`).

```bash
ls -la
```

Commonly used combination.

---

## Change Directory

```bash
cd folder_name
```

Moves into a directory.

Example:

```bash
cd projects
```

---

### Move Up One Directory

```bash
cd ..
```

Example:

```
/home/user/projects
```

becomes

```
/home/user
```

---

### Go to Home Directory

```bash
cd ~
```

or simply:

```bash
cd
```

---

### Go to Root Directory

```bash
cd /
```

Root is the top-level directory in Linux.

---

# Creating Files and Directories

## Create a Directory

```bash
mkdir directory_name
```

Example:

```bash
mkdir new_project
```

---

### Create Nested Directories

```bash
mkdir -p project/src/components
```

The `-p` flag creates parent directories if they do not exist.

---

## Create an Empty File

```bash
touch filename.txt
```

Example:

```bash
touch notes.md
```

Commonly used to create:
- placeholder files
- markdown notes
- configuration files

---

# Copying Files and Directories

## Copy a File

```bash
cp source_file destination
```

Example:

```bash
cp notes.md backup_notes.md
```

---

## Copy a Directory

```bash
cp -r directory_name new_directory
```

The `-r` flag means **recursive**, which copies everything inside the directory.

Example:

```bash
cp -r project project_backup
```

---

# Moving and Renaming Files

## Move a File

```bash
mv file.txt folder/
```

Example:

```bash
mv notes.md docs/
```

---

## Rename a File

```bash
mv old_name.txt new_name.txt
```

Example:

```bash
mv draft.md final.md
```

The `mv` command handles both **moving and renaming**.

---

# Deleting Files and Directories

## Delete a File

```bash
rm file.txt
```

Example:

```bash
rm notes.md
```

⚠️ **Important:** This permanently deletes the file.

---

## Delete a Directory

```bash
rm -r directory_name
```

Example:

```bash
rm -r old_project
```

---

### Force Delete

```bash
rm -rf directory_name
```

Flags:

| Flag | Meaning |
|-----|------|
| `-r` | recursive deletion |
| `-f` | force (no confirmation) |

⚠️ Use carefully — this can delete entire directory trees.

---

# Viewing File Contents

## Display File Contents

```bash
cat filename.txt
```

Example:

```bash
cat notes.md
```

Useful for quickly reading small files.

---

## Scroll Through Files

```bash
less filename.txt
```

Example:

```bash
less large_log.txt
```

Features:
- scroll with arrow keys
- search using `/`
- exit with `q`

---

# Searching

## Search for Files

```bash
find . -name "filename"
```

Example:

```bash
find . -name "config.json"
```

`.` means search from the current directory.

---

# Useful Shortcuts

| Shortcut | Meaning |
|------|------|
| `tab` | autocomplete commands or filenames |
| `↑` | previous command |
| `ctrl + c` | cancel command |
| `clear` | clear terminal screen |

---

# Example Workflow

Example workflow for creating a project directory:

```bash
mkdir project
cd project
mkdir src
touch README.md
ls
```

Resulting structure:

```
project/
├── README.md
└── src/
```

---

# Summary of Core Commands

| Command | Purpose |
|------|------|
| `pwd` | show current directory |
| `ls` | list directory contents |
| `cd` | change directory |
| `mkdir` | create directory |
| `touch` | create file |
| `cp` | copy files |
| `mv` | move or rename files |
| `rm` | delete files |
| `cat` | display file contents |
| `less` | view files interactively |
| `find` | search for files |

---

# Why These Commands Matter

These commands form the **core toolkit for interacting with Linux systems** and are essential for:

- software development
- server management
- DevOps workflows
- Git and version control
- working on remote machines via SSH