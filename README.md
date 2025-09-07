# Shell Scripting Tutorial

Welcome to the **Shell Scripting Tutorial** repository!  
This guide is designed for **absolute beginners** who want to learn how to automate tasks in Linux using shell scripts.

---

# 📚 Table of Contents

1. [Shell Scripting Fundamentals](#1️⃣-shell-scripting-fundamentals)
2. [Variables](#2️⃣-variables)
3. [User Input and Read](#3️⃣-user-input-and-read)
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

### 📄 1️⃣ Create a New File

```bash
vim my_script.sh
```

> If the file doesn’t exist, it will be created.

---

### ✍️ 2️⃣ Enter Insert Mode

* Press `i` to enter insert mode

---

### 💬 3️⃣ Write Your Script

```bash
# ! /bin/bash
# This is my first bash
echo "Hello Linux User! "
echo "Today's Time and Date is : "
date
```

---

### ❌ 4️⃣ Exit Insert Mode

* Press `Esc` to switch back to command mode

---

### 💾 5️⃣ Save and Exit

```bash
:wq   # write & quit
```

> Optional commands:

* `:w` → Save only
* `:q!` → Quit without saving

---

### 🔓 6️⃣ Make Script Executable

```bash
chmod +x my_script.sh
```
Or 
 ```
 chmod 754 my_script.sh
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

### ▶️ 7️⃣ Run the Script

```bash
./my_script.sh
```

---

### 🚫 8️⃣ Run Without Making Executable

```bash
bash my_script.sh
```

---

### 📤 9️⃣ Example Output

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

---

### ✅ Valid Variable Names

These are allowed:

```bash
ABC
_AV_3
AV232
````

---

### ❌ Invalid Variable Names

These will cause errors:

```bash
2_AN     # Starts with a number
!ABD     # Contains !
$ABC     # Contains $
&QAID    # Contains &
```

> 📝 **Note:** Only underscores (`_`) are allowed as special characters in variable names. All other special characters have predefined meanings in Shell.

---

### 🛠️ 1️⃣ Defining a Variable

```bash
variable_name=<value>
```

> ⚠️ No spaces before or after `=`

### 📥 2️⃣ Accessing a Variable

Use `$` to access the value:

```bash
#!/bin/bash

first_name="Anik"
last_name="Dash"

echo "$first_name $last_name and date is $(date)"
```

🟢 **Output:**

```
Anik Dash
```

---

### ❌ 3️⃣ Unsetting a Variable

Use `unset` to delete a variable:

```bash
#!/bin/bash

name="Anik"
age=26
echo "$name $age"

unset age

echo "$name $age"
```

🟢 **Output:**

```
Anik 26
Anik 
```

> ⚠️ You **cannot unset a read-only variable**

---

### 🔒4️⃣ Read-Only Variable

A variable declared as `readonly` cannot be changed later.

```bash
#!/bin/bash

group="DevOps"
readonly group

echo "Group is: $group"

group="DevSecOps"  # This will cause an error
```

🟢 **Output:**

```
Group is : DevOps
./variable.sh: line 9: group: readonly variable
```

---

## 🧪 Example Script: All Concepts Together

```bash
#!/bin/bash

# Variable definitions
name="Anik Dash"
age=26

# Accessing variables
echo "Name is $name and age is $age."

# Read-only variable
blood_group="O+"
readonly blood_group
echo "Blood group is $blood_group"

# Trying to modify read-only variable
blood_group="B+"   # Will throw error

# Unsetting a variable
unset age
echo "After unsetting age..."
echo "Name is $name, blood group is $blood_group, age is $age"
```

---

# 3️⃣ User Input and Read

Shell scripts can take input from the user during execution using the `read` command. This makes scripts interactive and flexible.

### Taking Name as Input
```
#!/bin/bash

echo "Enter your name :"
read name
echo "Hello $name!"
```
🟢 **Output:**
```
Enter your name:
Anik
Hello Anik!
```

### Read Command arguments

- **Prompt String** `-p`
- **Password Input** `-s`
- **Changing the Delimiter** `IFS`
- **Parsing to the array** `-a`
- **Limiting Length of the Input** `-n`
- **Timed Input** `-t`

### 1️⃣ Prompt String (`-p`)

```bash
#!/bin/bash

read -p "Enter you OS name: " OS
echo "Your OS is: $OS"                      
````

🟢 **Output:**

```
Enter you OS name: Ubuntu
Your OS is: Ubuntu
```

---

### 2️⃣ Silent/Password Input (`-s`)

```bash
#!/bin/bash
echo "Enter your password: "
read -s
echo "Your password saved"
```

🟢 **Output:**

```
Enter your password:
Your password saved
```

---

#### 3️⃣ Changing the Delimiter (IFS)

```bash
#!/bin/bash

IFS="&" read OS1 OS2
echo "OS1 : $OS1"
echo "OS2 : $OS2"
```

🟢 **Input:**

```
Ubuntu&Windows
```

🟢 **Output:**

```
OS1 : Ubuntu
OS2 : Windows
```

---

### 4️⃣ Parsing to an Array (`-a`)

```bash
#!/bin/bash

echo "Enter a list of programming languages:"
read -a languages

echo "I like: ${languages[0]}, ${languages[1]}, and ${languages[2]}"
```

🟢 **Input:**

```
Bash Python C++
```

🟢 **Output:**

```
I like: Bash, Python, and C++
```

---

### 5️⃣ Limiting Length of the Input (`-n`)

```bash
#!/bin/bash

read -n 5 -p "Enter only 5 digit code: " digit
echo
echo "Your code is: $digit"                         
```

🟢 **Output (accepts only 4 characters):**

```
Enter only 5 digit code: 12340
Your code is: 12340
```

---

### 6️⃣ Timed Input (`-t`)

```bash
#!/bin/bash

read -t 5 -p "Enter Your username (Within 5 seconds) : " name
echo "Your username is : $name"
```

🟢 **Output (if typed within 5 seconds):**

```
Enter Your username (Within 5 seconds) : Anik
Your username is : Anik
```

🟡 **If no input:**

```
Username: 
```

---