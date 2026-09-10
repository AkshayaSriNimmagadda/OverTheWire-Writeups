# Bandit — Level 1 → Level 2

##  Objective

The goal of this level is to find the **password for the next level**. The password is stored in a file named `-` in the home directory.

Since the filename is a single hyphen (`-`), it can be confused with standard input by Linux commands. Therefore, we need to specify the file path correctly.

##  Commands Used

| Command | Meaning                                 |
| ------- | --------------------------------------- |
| `ssh`   | Connect to a remote server              |
| `ls`    | List files and directories              |
| `cat`   | Display file contents                   |
| `./`    | Specify a file in the current directory |
| `exit`  | Exit the current session                |

##  Solution

### Step 1️: Connect to the Bandit Level 1 Server

After completing Level 0, I connected to the Bandit Level 1 account using SSH on port 2220.

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from the `readme` file in Level 0.

The login was successful, and I was connected to the Bandit Level 1 server.

----------------------------------------------------------------------------------------

### Step 2: List the Files

I checked the files available in the current directory using:

```bash
ls
```

The output showed:

```text
-
```

This means there is a file named `-` in the current directory.

----------------------------------------------------------------------------------------

### Step 3: Read the `-` File and Obtain the Password

Normally, we use `cat filename` to read a file. However, because `-` has a special meaning in many Linux commands, using:

```bash
cat -
```

does not read the file as expected. Instead, `-` is commonly interpreted as **standard input (stdin)**.

Therefore, I specified the file using its relative path:

```bash
cat ./-
```

The command displayed the contents of the `-` file.

 The contents of the file contain the **PASSWORD** required to log in to Bandit Level 2.

I copied the password for the next login.

----------------------------------------------------------------------------------------

### Step 4: Exit and Log in to Level 2

After that, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 2 account:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

When prompted for the **password**, I entered the password obtained from the `-` file.

The login was successful, and I was now connected to the **Bandit Level 2** server.

##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cat`** — Displaying the contents of a file.
* **`./`** — Specifying a file in the current directory.
* **Special filenames** — A filename such as `-` can have a special meaning to Linux commands.
* **Standard input (`stdin`)** — `-` is commonly used by Linux commands to represent input from the terminal.
