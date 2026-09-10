# Bandit — Level 7 → Level 8

## 🎯 Objective

The goal of this level is to find the password for the next level. The password is stored in the file named `data.txt` next to the word `millionth`.

We need to search the file and find the line containing the word `millionth`.

## 🛠️ Commands Used

| **Command** | **Meaning**                |
| ----------- | -------------------------- |
| `ssh`       | Connect to a remote server |
| `ls`        | List files and directories |
| `grep`      | Search for specific text   |
| `cat`       | Display file contents      |
| `exit`      | Exit the current session   |

## 🔍 Solution

### Step 1️: Connect to the Bandit Level 7 Server

After completing Level 6, I connected to the Bandit Level 7 account using SSH on port 2220.

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained in Level 6.

The login was successful, and I was connected to the Bandit Level 7 server.

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

### Step 3: Search for the Word `millionth`

The file contains a large amount of text, so instead of checking each and every line manually, I used the `grep` command.

```bash
grep "millionth" data.txt
```

The command displayed the line containing `millionth` followed by the **PASSWORD**.

I copied the password for the next login.

### Step 4: Exit and Log in to Level 8

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 8 account:

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from `data.txt`.

The login was successful, and I was now connected to the Bandit Level 8 server.

## 🧠 Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`grep`** — Searching for specific text inside files.
* **`cat`** — Displaying file contents.
* **Searching large files** — Using `grep` is faster than manually checking every line.
* Using the password obtained from one level to access the next level.
