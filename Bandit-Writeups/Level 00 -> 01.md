##🎯 Bandit — Level 0 → Level 1

## Objective

The goal of this level is to connect to the **Bandit Level 0** server using SSH and find the password to log into **Level 1**.

## Commands Used

| Command | Meaning                    |
| ------- | -------------------------- |
| `ssh`   | Connect to a remote server |
| `ls`    | List files and directories |
| `cat`   | Display file contents      |
| `exit`  | Exit the current session   |


#  Solution

## Step 1️: Connect to the Bandit Server

First, I connected to the Bandit server using SSH on port `2220`.

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

**Meaning:**

* `ssh` → Connects to a remote server
* `bandit0` → Username
* `bandit.labs.overthewire.org` → Server address
* `-p 2220` → Connects using port `2220`

The password provided for **Level 0** is:

```text
bandit0
```

After entering the password, the connection was established.

---

## Step 2: List the Files

After logging in, I checked the files using the following command:

```bash
ls
```


This showed that there was a file named `readme` in the current directory.

---

## Step 3: Read the `readme` File

I used the `cat` command to display the contents of the file:

```bash
cat readme
```

This displayed the contents of the `readme` file and those contents were **PASSWORD** for the Level 1.

I copied the password to use for the next login.

---

## Step 4: Exit the Current SSH Session

After obtaining the password, I exited the current SSH session:

```bash
exit
```

---

## Step 5: Log in to Level 1

Next, I connected to the **Bandit Level 1**:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier and therefore I was connected to **Bandit Level 1** server.



#  Concepts Learned

* **SSH** — Connecting to a remote server
* **`ls`** — Listing files
* **`cat`** — Reading file contents
* **`exit`** — Closing an SSH session
