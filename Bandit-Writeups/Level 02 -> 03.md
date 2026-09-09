# Bandit — Level 2 → Level 3

## 🎯 Objective

The goal of this level is to find the password for the next level. The password is stored in a file named `--spaces in this filename--` in the home directory.

Since the filename contains **spaces**, we need to handle the filename correctly when using Linux commands.

## 🛠️ Commands Used

| Command | Meaning                                 |
| ------- | --------------------------------------- |
| `ssh`   | Connect to a remote server              |
| `ls`    | List files and directories              |
| `cat`   | Display file contents                   |
| `./`    | Specify a file in the current directory |
| `exit`  | Exit the current session                |

## 🔍 Solution

### Step 1️: Connect to the Bandit Level 2 Server

After completing Level 1, I connected to the Bandit Level 2 account using SSH on port 2220.

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained in Level 1.

The login was successful, and I was connected to the Bandit Level 2 server.

----------------------------------------------------------------------------------------

### Step 2: List the Files

I checked the files available in the current directory using:

```bash
ls
```

The output showed:

```text
--spaces in this filename--
```

This means there is a file named `--spaces in this filename--` in the current directory.

----------------------------------------------------------------------------------------

### Step 3: Read the File and Obtain the Password

The filename contains **spaces** and starts with `--`, so we need to specify it correctly.

`./` tells Linux that the file is in the **current directory**, while quotes tell the shell to treat the entire name as **one filename**.

```bash
cat "./--spaces in this filename--"
```

The command displayed the **PASSWORD** required to log in to Bandit Level 3.

I copied the password for the next login.

----------------------------------------------------------------------------------------

### Step 4: Exit and Log in to Level 3

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 3 account:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from the `--spaces in this filename--` file.

The login was successful, and I was now connected to the Bandit Level 3 server.

## 🧠 Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cat`** — Displaying the contents of a file.
* **Spaces in filenames** — Spaces separate arguments in the Linux shell.
* **Quotes (`" "`)** — Used to treat a filename containing spaces as a single argument.
* **`./`** — Used to specify a file in the current directory.

