# 🎯Bandit — Level 10 → Level 11

## Objective

The goal of this level is to find the password for the next level. The password is stored in the file `data.txt`, which contains Base64 encoded data.

## Commands Used

| **Command** | **Meaning**                    |
| ----------- | ------------------------------ |
| `ssh`       | Connect to a remote server     |
| `ls`        | List files and directories     |
| `cat`       | Display the contents of a file |
| `base64`    | Encode or decode Base64 data   |
| `exit`      | Exit the current session       |

## Solution

### Step 1️: Connect to the Bandit Level 10 Server

After completing Level 9, I connected to the Bandit Level 10 account using SSH on port 2220.

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained in Level 9 and was connected to the Bandit Level 10 server.

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

The output contained Base64 encoded data.

---

### Step 4: Decode the Base64 Data

Since the file contains Base64 encoded data, I decoded it using:

```bash
base64 -d data.txt
```

###  Command Explanation

* `base64` → Used to encode or decode Base64 data.
* `-d` → Decodes the given Base64 data.
* `data.txt` → The file containing the Base64 encoded data.

The command displayed the decoded text containing the **PASSWORD** for Bandit Level 11.

---

### Step 5: Exit and Log in to Level 11

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 11 account:

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier and was connected to the Bandit Level 11 server.

## Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cat`** — Displaying the contents of a file.
* **Base64 Encoding** — A method of representing data using a set of 64 characters.
* **`base64 -d`** — Decoding Base64 encoded data.
* **`exit`** — Exiting the current SSH session.
