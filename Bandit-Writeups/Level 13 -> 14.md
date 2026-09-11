# 🎯Bandit — Level 13 → Level 14

## Objective

The goal of this level is to find the password for the next level. The password for Bandit Level 14 is stored in `/etc/bandit_pass/bandit14`.

However, the password cannot be accessed directly as `bandit13`. Instead, an SSH private key is provided in the home directory. I used this private key to log in to the `bandit14` account.

## Commands Used

| **Command** | **Meaning**                          |
| ----------- | ------------------------------------ |
| `ssh`       | Connect to a remote server using SSH |
| `ls`        | List files and directories           |
| `cat`       | Display the contents of a file       |
| `exit`      | Exit the current session             |

## Solution

### Step 1️: Connect to the Bandit Level 13 Server

After completing Level 12, I connected to the Bandit Level 13 account using SSH on port 2220.

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained in Level 12 and was connected to the Bandit Level 13 server.

---

### Step 2: List the Files

I checked the files available using:

```bash
ls
```

The output showed:

```text
sshkey.private
```

This showed that an SSH private key named `sshkey.private` was available in the home directory.

---

### Step 3: Use the SSH Private Key

I used the private key to log in directly to the `bandit14` account:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

### 📖 Command Explanation

* `ssh` → Used to connect to a remote server.
* `-i sshkey.private` → Specifies the private SSH key to use for authentication.
* `bandit14@localhost` → Connects to the `bandit14` account on the local server.
* `-p 2220` → Specifies port `2220` used by the Bandit SSH server.

The SSH private key allowed me to authenticate as `bandit14` without entering the Bandit Level 14 password.

---

### Step 4: Read the Password File

After successfully logging in as `bandit14`, I displayed the password file using:

```bash
cat /etc/bandit_pass/bandit14
```

The command displayed the **PASSWORD** for Bandit Level 14.

---

### Step 5: Exit the SSH Session

After obtaining the password, I exited the current SSH session:

```bash
exit
```

## Concepts Learned

* **SSH** — Connecting securely to a remote server.
* **SSH Private Key** — A private key can be used to authenticate to an SSH server without using a password.
* **`-i` option** — Specifies the identity/private key file used for SSH authentication.
* **`localhost`** — Refers to the current machine/server.
* **`cat`** — Displaying the contents of a file.
* **SSH Port `2220`** — The port used by the Bandit SSH server.
