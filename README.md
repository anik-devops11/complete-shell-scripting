# Shell Scripting Tutorial

Welcome to the **Shell Scripting Tutorial** repository!  
This guide is designed for **absolute beginners** who want to learn how to automate tasks in Linux using shell scripts.

---

# 📚 Table of Contents

1. [Shell Scripting Fundamentals](#1️⃣-shell-scripting-fundamentals)
2. [Variables](#2-variables)
3. [User Input and Read](#3-user-input-and-read)
4. [Conditional Statements (if/else)](#4-conditional-statements-ifelse)
5. [Loops (for, while, until)](#5-loops-for-while-until)
6. [Functions](#6-functions)
7. [File Handling](#7-file-handling)
8. [Command Line Arguments](#8-command-line-arguments)
9. [Exit Status and Error Handling](#9-exit-status-and-error-handling)
10. [Practical Examples](#10-practical-examples)

---

# 1️⃣ Shell Scripting Fundamentals

### What is a Shell Script?
A shell script is a text file (`.sh`) that includes a sequence of commands that will be executed by a shell (like Bash). Shell scripts allows for automation that enables one to create reusable, executable programs for tasks that would require manual command-line work.

### Why Shell Scripts?
- 🔄 **Automation**: Tasks that are repetitive, like backups, cleanups and deployments can be fully automated.
- ✅ **Reliability**: You run the same commands, in the same order every time, so you always get the same result. Loss of human error.
- ⚡ **Efficiency**: You can combine and chain commands to build complex workflows utilizing super simple tools.
- 🌐 **Native & Lightweight**: Shells are installed in every Unix/Linux system and have no dependencies.
- 🛠️ **DevOps Basic**: Shell scripts are the core of any administrative tasks, monitoring and automation of infrastructure.

---

### 🐚 Types of Shells

- `bash` – Bourne Again Shell (most common)  
- `sh` – Original Bourne Shell  
- `zsh` – Z Shell (popular with power users)  
- `ksh` – Korn Shell  

🧪 **Check your current shell**:
```bash
echo $0
```
## 🛠️ How to Create and Run a Shell Script

Learn how to create, edit, and execute a shell script using `vim`.

---

### 📄 1. Create a New File

```bash
vim my_script.sh
```

> If the file doesn’t exist, it will be created.

---

### ✍️ 2. Enter Insert Mode

* Press `i` to enter insert mode

---

### 💬 3. Write Your Script

```bash
# ! /bin/bash
# This is my first bash
echo "Hello Linux User! "
echo "Today's Time and Date is : "
date
```

---

### ❌ 4. Exit Insert Mode

* Press `Esc` to switch back to command mode

---

### 💾 5. Save and Exit

```bash
:wq   # write & quit
```

> Optional commands:

* `:w` → Save only
* `:q!` → Quit without saving

---

### 🔓 6. Make Script Executable

```bash
chmod +x my_script.sh
```
Or 
 ```
 chmod 754
```
In Linux, the `chmod` command is used to control who can **read**, **write**, or **execute** a file or script.
| Permission | Number | Meaning         |
| ---------- | ------ | --------------- |
| `0`        | ---    | No access       |
| `1`        | --x    | Execute only    |
| `2`        | -w-    | Write only      |
| `3`        | -wx    | Write + Execute |
| `4`        | r--    | Read only       |
| `5`        | r-x    | Read + Execute  |
| `6`        | rw-    | Read + Write    |
| `7`        | rwx    | All access      |

---

### ▶️ 7. Run the Script

```bash
./my_script.sh
```

---

### 🚫 8. Run Without Making Executable

```bash
bash my_script.sh
```

---

### 📤 9. Example Output

```
Hello Linux User!
Today's Time and Date is .
Fri sep 5 AM +06 2025
```
## 💬 Comments in Shell Scripting

In shell scripting, comments help make scripts easier to understand by explaining what the code does. Comments are **ignored by the shell** during execution.

---

### 🧵 Single-Line Comments

Use the `#` symbol at the beginning of a line to write a comment.

```bash
# This is a single-line comment
echo "Hello, World!"  # This comment is on the same line as a command
```
---

### 📄 Multi-Line Comments (Simulated)

Although Bash doesn't support traditional multi-line comments, you can simulate them using a **here-document**:

```bash
<<comment
This is a multi-line comment.
It won’t be executed.
comment
```
> ⚠️ Note: The starting and ending `comment` must be **exactly the same**, and there should be **no leading spaces or tabs** on the line.

# 2️⃣ Variables

A **shell variable** is a named storage location used to hold data like numbers, strings, filenames, or command outputs. It acts as a pointer to values in memory and plays a key role in writing dynamic and reusable shell scripts.
