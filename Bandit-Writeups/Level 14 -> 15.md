# 🎯Bandit — Level 14 → Level 15

## Objective

The goal of this level is to find the password for **Level 15** by submitting the **current password to port 30000 on localhost**.

## Commands Used

| **Command** | **Meaning**                                   |
| ----------- | --------------------------------------------- |
| `ssh`       | Connect to a remote server                    |
| `nc`        | Connect to a network service using TCP or UDP |
| `cat`       | Display the contents of a file                |
| `exit`      | Exit the current session                      |

## Solution

### Step 1️: Connect to the Bandit Level 14 Server

Since the SSH private key was obtained in the previous level, we can use it to directly log in to Level 14.

```bash
ssh -i ./sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

After authentication, we are logged in as:

````
bandit14@bandit:~$
`````

---

### Step 2: Find the current password

The current Level 14 password is stored in:

```text
/etc/bandit_pass/bandit14
```

I displayed the contents of the file using:

```bash
cat /etc/bandit_pass/bandit14
```
This command gives the password of the current Level 14.

---

### Step 3: Submit the Password to Port 30000

The current password must be submitted to port 3000, using the command:

````bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
`````

# Command Explanation

`cat /etc/bandit_pass/bandit14` → reads the current Level 14 password.
`|` → sends the output of cat as input to the next command.
`nc` → Netcat, a tool used to communicate with network services.
`localhost` → refers to the current Bandit server.
`30000` → the port where the required service is running.

---

Thi gives the **PASSWORD** required for Bandit Level 15.

---

### Step 4: Exit and Log in to Level 15

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 15 account:

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier and was connected to the Bandit Level 15 server.

## Concepts Learned

* **SSH** — Connecting to a remote server.
* **`cat`** — Displaying the contents of a file.
* **`nc` (Netcat)** — Connecting to network services.
* **`localhost`** — Refers to the current machine/server.
