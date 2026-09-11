# 🎯Bandit — Level 13 → Level 14

## Objective

The goal of this level is to find the password for **Bandit Level 14**. The password is stored in:

```text
/etc/bandit_pass/bandit14
```

However, as `bandit13`, the password file cannot be accessed directly. Instead, an **SSH private key** named `sshkey.private` is provided in the home directory. I used this private key to log in to the `bandit14` account and then accessed the password file.

## Commands Used

| **Command** | **Meaning**                          |
| ----------- | ------------------------------------ |
| `ssh`       | Connect to a remote server using SSH |
| `ls`        | List files and directories           |
| `cat`       | Display the contents of a file       |
| `exit`      | Exit the current SSH session         |

## Solution

### Step 1️: Connect to the Bandit Level 13 Server

After completing Level 12, I connected to the Level 13.

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

I entered the password obtained from Level 12 and was connected to the Level 13 server.

---

### Step 2: List the Files

I checked the files available in the home directory using:

```bash
ls
```

The output showed:

```text
sshkey.private
```

This is an **SSH private key** that can be used to authenticate to the `bandit14` account.

---

### Step 3: Use the SSH Private Key

I used the private key to connect to the `bandit14` account using the command:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

###  Command Explanation

* `ssh` → Used to connect to a remote server.
* `-i sshkey.private` → Specifies the private SSH key used for authentication.
* `bandit14@localhost` → Connects to the `bandit14` account on the local Bandit server.
* The private key allowed me to authenticate as `bandit14` without entering the Bandit Level 14 password.

---

### Step 4: Read the Password File

After successfully logging in as `bandit14`, I accessed the password file using:

```bash
cat /etc/bandit_pass/bandit14
```

This command displayed the **PASSWORD** for Bandit Level 14.


---

### Step 5: Exit the SSH Session

After obtaining the password, I exited the current SSH session:

```bash
exit
```

## Concepts Learned

* **SSH** — Used to securely connect to a remote server.
* **SSH Private Key** — Can be used for authentication instead of a password.
* **`-i` option** — Specifies the identity/private key file used for SSH authentication.
* **`localhost`** — Refers to the current machine/server.
* **`cat`** — Used to display the contents of a file.
* **Key-Based Authentication** — SSH can authenticate users using a private key instead of a password.
