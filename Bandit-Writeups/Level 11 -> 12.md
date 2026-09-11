# 🎯Bandit — Level 11 → Level 12

## Objective

The goal of this level is to find the password for the next level. The password is stored in the file `data.txt`, where all lowercase (`a-z`) and uppercase (`A-Z`) letters have been rotated by 13 positions.

This type of substitution is known as **ROT13**.

## Commands Used

| **Command** | **Meaning**                     |
| ----------- | ------------------------------- |
| `ssh`       | Connect to a remote server      |
| `ls`        | List files and directories      |
| `cat`       | Display the contents of a file  |
| `tr`        | Translate or replace characters |
| `exit`      | Exit the current session        |

## Solution

### Step 1️: Connect to the Bandit Level 11 Server

After completing Level 10, I connected to the Bandit Level 11 account using SSH on port 2220.

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained in Level 10 and was connected to the Bandit Level 11 server.

---

### Step 2: List the Files

I checked the files available using:

```bash
ls
```

The output showed:

```text
data.txt
```

This showed that there is a file named `data.txt` in the current directory.

---

### Step 3: View the File

I displayed the contents of `data.txt` using:

```bash
cat data.txt
```

The output contained a text where the letters were rotated by 13 positions.

---

### Step 4: Decode the ROT13 Text

Since the letters were rotated by 13 positions, I used the `tr` command to decode the text:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### 📖 Command Explanation

* `cat data.txt` → Displays the contents of `data.txt`.
* `|` → Sends the output of `cat` to the next command.
* `tr` → Translates or replaces characters.
* `'A-Za-z'` → Represents all uppercase and lowercase English letters.
* `'N-ZA-Mn-za-m'` → Applies the ROT13 character substitution pattern..

The command decoded the text and displayed the **PASSWORD** for Bandit Level 12.

---

### Step 5: Exit and Log in to Level 12

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 12 account:

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier and was connected to the Bandit Level 12 server.

## Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cat`** — Displaying the contents of a file.
* **`tr`** — Translating or replacing characters.
* **ROT13** — A substitution cipher that rotates each letter by 13 positions.
* **Pipe (`|`)** — Passing the output of one command as input to another command.
