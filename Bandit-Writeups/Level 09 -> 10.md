# Bandit — Level 9 → Level 10

## 🎯 Objective

The goal of this level is to find the password for the next level. The password is stored in the file `data.txt` among several **human-readable strings**, and it is preceded by several `=` characters.

## 🛠️ Commands Used

| **Command** | **Meaning**                             |
| ----------- | --------------------------------------- |
| `ssh`       | Connect to a remote server              |
| `ls`        | List files and directories              |
| `strings`   | Extract readable text from binary files |
| `grep`      | Search for specific text                |
| `exit`      | Exit the current session                |

## 🔍 Solution

### Step 1️: Connect to the Bandit Level 9 Server

After completing Level 8, I connected to the Bandit Level 9 account using SSH on port 2220.

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained in Level 8.

The login was successful, and I was connected to the Bandit Level 9 server.

### Step 2: List the Files

I checked the files available in the current directory using:

```bash
ls
```

The output showed:

```text
data.txt
```

This means there is a file named `data.txt` in the current directory.

### Step 3: Find the Readable Text

Since the objective says that the password is preceded by several `=` characters, I searched for `=` using `grep`:

```bash
strings data.txt | grep "="
```

### 📖 Command Explanation

* `strings data.txt` → Extracts readable text from `data.txt`.
* `|` → Sends the output of `strings` to the next command.
* `grep "="` → Searches the extracted text for lines containing `=`.

The command displayed the line containing the **PASSWORD** for Bandit Level 10.

I copied the password for the next login.

### Step 4: Exit and Log in to Level 10

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 10 account:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from `data.txt`.

The login was successful, and I was now connected to the Bandit Level 10 server.

## 🧠 Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`strings`** — Extracting human-readable text from binary data.
* **`grep`** — Searching for specific text.
* **Pipe (`|`)** — Passing the output of one command as input to another command.
* Searching binary files for readable information.
