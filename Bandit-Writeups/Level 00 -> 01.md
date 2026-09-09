# 🔐 Bandit — Level 0 → Level 1

## 🎯 Objective

The goal of this level is to connect to the **Bandit Level 0** server using SSH and find the password required to log in to **Level 1**.

---

## 🛠️ Commands Used

|  Command |  Meaning                    |
| ---------- | ----------------------------- |
| `ssh`      |  Connect to a remote server |
| `ls`       |  List files and directories |
| `cat`      |  Display file contents      |
| `exit`     |  Exit the current session   |

---

# 🔍 Solution

## Step 1️:Connect to the Bandit Server

First, I connected to the Bandit server using SSH on port `2220`.

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

 The password provided for **Level 0** is:

```text
bandit0
```

After entering the password, the connection was successfully established.

---

## Step 2:List the Files

After logging in, I checked the files available in the current directory using:

```bash
ls
```
The output:

```text
readme
```

This showed that there was a file named `readme` in the current directory.

---

## Step 3:Read the `readme` File

I used the `cat` command to display the contents of the file:

```bash
cat readme
```

 This displayed the contents of the `readme` file.

 The file contained the **password for the next level(Level 1)**.

I copied the password to use for the next login.

---

## step 4:Exit the Current SSH Session

After obtaining the password, I exited the current SSH session:

```bash
exit
```
---

## Step 5:Log in to Level 1

Next, I connected to the **Bandit Level 1** account:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

 When prompted for the password, I entered the password obtained from the `readme` file.

 The login was successful, and I was now connected to the **Bandit Level 1** server.

---

# 🧠 Concepts Learned

*  **SSH** — Connecting to a remote server
*  **`ls`** — Listing files
*  **`cat`** — Reading file contents
*  **`exit`** — Closing an SSH session
*  Using the password obtained from one level to access the next level

---


🎓 **Main Lesson:** Always start by exploring the environment and checking the available files before trying more advanced techniques.

