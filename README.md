# Shell Scripting Tutorial

Welcome to the **Shell Scripting Tutorial** repository!  
This guide is designed for **absolute beginners** who want to learn how to automate tasks in Linux using shell scripts.

---

# 📚 Table of Contents

1. [Shell Scripting Fundamentals](#1️⃣-shell-scripting-fundamentals)
2. [Variables](#2️⃣-variables)
3. [User Input and Read](#3️⃣-user-input-and-read)
4. [Conditional Statements](#4️⃣-conditional-statements)
5. [Shell Scripting Loops](#5️⃣-shell-scripting-loops)
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

# 4️⃣ Conditional Statements

Conditional statements allow your script to **make decisions** based on conditions. They help execute different commands depending on whether a condition is **true or false**.

---

### 📌 Basic Syntax

```bash
if [ condition ]
then
    # commands
fi
````

With `else`:

```bash
if [ condition ]
then
    # commands if true
else
    # commands if false
fi
```

With `elif`:

```bash
if [ condition1 ]
then
    # commands if condition1 is true
elif [ condition2 ]
then
    # commands if condition2 is true
else
    # commands if none are true
fi
```

---

### 🧪 Example 1: Simple `if`

```bash
#!/bin/bash

num=10

if [ $num -gt 5 ]
then
    echo "$num is greater than 5"
fi
```

---

### 🧪 Example 2: `if-else`

```bash
#!/bin/bash

echo "Enter your age:"
read age

if [ $age -ge 18 ]
then
    echo "You are an adult."
else
    echo "You are underage."
fi
```

---

### 🧪 Example 3: `if-elif-else`

```bash
#!/bin/bash

echo "Enter a number:"
read num

if [ $num -gt 0 ]
then
    echo "Positive number"
elif [ $num -lt 0 ]
then
    echo "Negative number"
else
    echo "Zero"
fi
```

---

### 🧠 Common Comparison Operators

| Operator | Meaning             |
| -------- | ------------------- |
| `-eq`    | Equal               |
| `-ne`    | Not equal           |
| `-gt`    | Greater than        |
| `-lt`    | Less than           |
| `-ge`    | Greater or equal    |
| `-le`    | Less or equal       |
| `==`     | Equal (strings)     |
| `!=`     | Not equal (strings) |

---

### 🔎 String Comparison Example

```bash
#!/bin/bash

str1="Anik"
str2="Dash"

if [ "$str1" == "$str2" ]
then
    echo "Strings are equal"
else
    echo "Strings are different"
fi
```

---

## 🗂️ File Test Operators

| Operator  | Description           |
| --------- | --------------------- |
| `-e file` | True if file exists   |
| `-f file` | True if regular file  |
| `-d file` | True if directory     |
| `-r file` | True if readable      |
| `-w file` | True if writable      |
| `-x file` | True if executable    |
| `-s file` | True if not empty     |
| `-L file` | True if symbolic link |

#### 🧪 Example: File Test

```bash
#!/bin/bash

file="hello.txt"

if [ -e "$file" ]; then
    echo "$file exists."
else
    echo "$file does not exist."
fi
```

---

## 🔹 Logical Operators

| Operator | Meaning                            |    |                   |
| -------- | ---------------------------------- | -- | ----------------- |
| `!`      | NOT → reverses a condition         |    |                   |
| `-a`     | AND → true if both conditions true |    |                   |
| `-o`     | OR → true if any condition true    |    |                   |
| `&&`     | AND (in \[\[ … ]])                 |    |                   |


#### 🧪 Example: Logical Operators

```bash
#!/bin/bash

num=15

# Using -a (AND)
if [ $num -gt 10 -a $num -lt 20 ]; then
    echo "$num is between 10 and 20"
fi

# Using -o (OR)
if [ $num -lt 10 -o $num -gt 20 ]; then
    echo "$num is outside 10-20 range"
else
    echo "$num is inside 10-20 range"
fi

# Using ! (NOT)
if [ ! -e "data.txt" ]; then
    echo "data.txt does not exist"
fi
```

> 💡 Tip: Using `[[ … ]]` allows `&&` and `||` for cleaner syntax:

```bash
if [[ $num -gt 10 && $num -lt 20 ]]; then
    echo "Inside range"
fi
```

---

### ⚠️ Tips for Conditional Statements

* Always include **spaces** inside `[ ]` → `[ $a -gt 10 ]` ✅
* Quote variables `"${var}"` to prevent errors if empty
* Use `fi` to close every `if` block
* Combine multiple conditions with **logical operators** for powerful scripts

---

# 5️⃣ Shell Scripting Loops

Loops in shell scripting allow you to execute a block of code repeatedly based on a condition or a set of values. 

---

## 1️⃣ For Loop

The for loop iterates over a list of items (e.g., strings, numbers, files) and executes a block of code for each item.

### 📌 Basic Syntax
```bash
for variable in list; do
    # Commands
done
````

### 1.1 Example: Iterating Over a List of Names 📝

```bash
#!/bin/bash
for name in "AWS" "Linux" "Git" "Bash"; do
    echo "Tools Name: $name"
done
```

**Output:**

```
Tools name: AWS
Tools name: Linux
Tools name: Git
Tools name: Bash
```

### 1.2 Example: Listing All Files in the Current Directory 📂

```bash
#!/bin/bash
for file in *; do
    echo "File: $file"
done
```

**Output:** (Depends on files in the directory, e.g., script.sh, input.txt)

```
File: script.sh
File: input.txt
```

### 1.3 Example: Listing Specific Files (e.g., .txt Files) 📝

```bash
#!/bin/bash
for file in *.txt; do
    echo "Text file: $file"
done
```

**Output:** (For .txt files like note1.txt, note2.txt)

```
Text file: note1.txt
Text file: note2.txt
```

### 1.4 Example: Using a Numerical Range 🔢

```bash
#!/bin/bash
for num in {1..5}; do
    echo "Number: $num"
done
```

**Output:**

```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

**Use Case:** Use for loops when you have a fixed list of items (names, files, or numbers) or know the number of iterations in advance.

---

## 2️⃣ While Loop

The while loop executes a block of code as long as a condition is true.

### 📌 Basic Syntax
```bash
while condition; do
    # Commands
done
```

### 2.1 Example: Print Number's Multiplication Table ✖️

```bash
#!/bin/bash
read -p "please enter a number " number
initNumber=1
while [[ ${initNumber} -le 10 ]]
do
    echo "$initNumber * $number = $((initNumber*number))"
    ((initNumber++))
done
```

**Output:**

```
please enter a number 5
1 * 5 =  5
2 * 5 =  10
3 * 5 =  15
4 * 5 =  20
5 * 5 =  25
6 * 5 =  30
7 * 5 =  35
8 * 5 =  40
9 * 5 =  45
10 * 5 =  50
```

### 2.2 Example: Iterating Over a List of Names 🧑‍💻

```bash
#!/bin/bash
names="AWS Git Linux Bash"
while IFS= read -r name; do
    echo "Name: $name"
done <<< "$names"
```

**Output:**

```
Name: AWS Git Linux Bash
```

### 2.3 Example: Counting Numbers 🔢

```bash
#!/bin/bash
num=1
while [ $num -le 5 ]; do
    echo "Number: $num"
    ((num++))
done
```

**Output:**

```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

### 2.4 Example: Reading a File Line by Line 📄

```bash
#!/bin/bash
while IFS= read -r line; do
    echo "Line: $line"
done < input.txt
```

**Output:** (Depends on input.txt, e.g., apple, banana, orange)

```
Line: apple
Line: banana
Line: orange
```

---

## 3️⃣ Until Loop ⏳

The `until` loop executes a block of code **until a condition becomes true**. It is the opposite of `while`.

### 3.1 Syntax ✅

```bash
until [ condition ]
do
    # commands
done
```

### 3.2 Example: Counting from 1 to 5 🔢

```bash
#!/bin/bash
count=1
until [ $count -gt 5 ]
do
    echo "Count: $count"
    ((count++))
done
```

**Output:**

```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
```

### 3.3 Example: User Input Until Correct Number 🎯

```bash
#!/bin/bash
number=0
until [ $number -eq 5 ]
do
    read -p "Guess the number (1-10): " number
done
echo "Congrats! You guessed 5."
```

### 3.4 Key Point 💡

* Loop continues **while the condition is false**.
* Once the condition becomes true, it exits.
