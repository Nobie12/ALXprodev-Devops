# 🐚 Advanced Shell Scripting: Automating Tasks and Managing Processes

## 📖 Overview

Shell scripting is a powerful tool for automating repetitive tasks by writing a sequence of commands in a script file. Mastering shell scripting allows you to handle automation, process control, system monitoring, backups, and much more.

---

## 🧱 Shell Scripting Basics

### 🔹 What is a Shell?

A **shell** is a command-line interpreter that provides the user interface for interacting with the operating system.

### 🔹 What is a Script?

A **script** is a plain text file containing a list of shell commands that the shell can execute in sequence.

---

## 1️⃣ Basic Syntax

### 🔸 Variables

Used to store data values.

```bash
name="Nobie"
echo "Hello, $name"
```

### 🔸 Control Structures

Use `if`, `else`, `for`, `while`, and `case` to control flow:

```bash
if [ "$name" == "Nobie" ]; then
  echo "Welcome, Nobie!"
else
  echo "Access Denied"
fi
```

### 🔸 Functions

Group commands into reusable blocks:

```bash
greet() {
  echo "Hello, $1"
}
greet "Alice"
```

### 📁 Example: Check if a Directory Exists

```bash
#!/bin/bash
DIRECTORY="/path/to/directory"

if [ -d "$DIRECTORY" ]; then
  echo "Directory exists."
else
  echo "Directory does not exist."
fi
```

## 2️⃣ Advanced Commands

Shell scripts often require powerful text-processing tools:

### 🔹 `grep` — Pattern Searching

```bash
grep -i "error" logfile.txt
```

### 🔹 `awk` — Text Processing Language

```bash
awk '{sum += $1} END {print sum}' numbers.txt
```

### 🔹 `sed` — Stream Editor

```bash
sed 's/old/new/g' file.txt
```

## 3️⃣ Process Management

Efficient process control is critical for advanced scripts.

### 🔸 Foreground vs Background

- **Foreground**: Blocks the terminal until done.
- **Background**: Runs independently.

```bash
long_task.sh &        # Run in background
fg %1                 # Bring job %1 to foreground
```

### 🔸 Job Control Commands

- `jobs` — List active jobs
- `fg` — Resume job in foreground
- `bg` — Resume job in background
- `kill` — Terminate a process

---

## 4️⃣ Automation Scripts

Automate backups, file operations, and monitoring tasks.

### 📁 Example: Daily Backup Script

```bash
#!/bin/bash
SOURCE="/path/to/source"
DEST="/path/to/destination"
DATE=$(date +%Y-%m-%d)

tar -czf "$DEST/backup-$DATE.tar.gz" "$SOURCE"
echo "Backup completed on $DATE" >> /var/log/backup.log
```

## 5️⃣ Error Handling

Robust scripts handle failures gracefully.

### 🔸 Exit Status

Check success/failure of the last command using `$?`.

### 🔸 Trap Command

Capture errors and signals:

```bash
#!/bin/bash
trap 'echo "An error occurred. Exiting..."; exit 1' ERR

mkdir /path/to/new_directory || exit 1
cp /path/to/source /path/to/destination || exit 1

echo "Operation completed successfully."
```

## ✅ Conclusion

Mastering advanced shell scripting unlocks the full power of automation and process management. By understanding:

- Advanced command usage
- Process control
- Error handling
- Script modularity

...you can write powerful, efficient, and maintainable scripts that greatly enhance your productivity as a developer or system administrator.

## 📎 Further Reading & Tools

- `man bash` – Official Bash documentation
- [Advanced Bash-Scripting Guide](https://tldp.org/LDP/abs/)
- `crontab` – Automate tasks using cron jobs
