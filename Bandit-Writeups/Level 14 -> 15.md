# 🎯Bandit — Level 14 → Level 15

## Objective

The goal of this level is to retrieve the password for the next level. The password for the current level must be submitted to **port 30000 on localhost**.

## Commands Used

| **Command** | **Meaning**                                   |
| ----------- | --------------------------------------------- |
| `ssh`       | Connect to a remote server                    |
| `nc`        | Connect to a network service using TCP or UDP |
| `cat`       | Display the contents of a file                |
| `exit`      | Exit the current session                      |

## Solution

### Step 1️: Connect to the Bandit Level 14 Server

After completing Level 13, I connected to the Bandit Level 14 account using SSH on port 2220.

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained in Level 13 and was connected to the Bandit Level 14 server.

---

### Step 2: Locate the Password File

The password for the current level is stored in the file:

```text
/etc/bandit_pass/bandit14
```

I displayed the contents of the file using:

```bash
cat /etc/bandit_pass/bandit14
```

This displayed the password for the Bandit Level 14 account.

---

### Step 3: Submit the Password to Port 30000

The level requires the current password to be submitted to port `30000` on `localhost`.

I used the `nc` command:

```bash
nc localhost 30000
```

After the connection was established, I entered the password obtained from:

```bash
cat /etc/bandit_pass/bandit14
```

The server responded with the password for **Bandit Level 15**.

---

### 📖 Command Explanation

* `cat /etc/bandit_pass/bandit14` → Displays the password of the current Bandit level.
* `nc localhost 30000` → Connects to port `30000` on the local machine.
* `localhost` → Refers to the current server.
* `30000` → The port where the Bandit service is listening.
* `nc` → Netcat, a command-line tool used to establish network connections.

The password was submitted to the service running on port `30000`, which returned the password required for Bandit Level 15.

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

When asked for the password, I entered the password obtained from the service on port `30000` and was connected to the Bandit Level 15 server.

## Concepts Learned

* **SSH** — Connecting to a remote server.
* **`cat`** — Displaying the contents of a file.
* **`nc` (Netcat)** — Connecting to network services through TCP or UDP.
* **`localhost`** — Refers to the current machine/server.
* **Port** — A logical endpoint used by network services.
* **TCP Connection** — A connection used to communicate reliably with a network service.
* **`exit`** — Exiting the current SSH session.
