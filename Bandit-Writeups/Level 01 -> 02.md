# 🎯 Bandit — Level 1 → Level 2

##  Objective

The goal of this level is to find the **password for the next level**. The password is stored in a file named `-` directory.
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

When asked for the password, I entered the password obtained earlier and was connected to Bandit Level 1 server.

----------------------------------------------------------------------------------------

### Step 2: List the Files

I checked the files available using:

```bash
ls
```

The output showed:

```text
-
```

This showed that there is a file named `-` in the current directory.

----------------------------------------------------------------------------------------

### Step 3: Read the `-` File and Obtain the Password

Since `-` has a another meaning in many Linux commands, using:

```bash
cat -
```

does not read the file. Instead, `-` is commonly known as **standard input (stdin)**.

Therefore, I specified the file using its relative path:

```bash
cat ./-
```

This command displayed the **PASSWORD** for Level 2.

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

When asked for the **password**, I entered the password obtained earlier and was connected to the **Bandit Level 2** server.

##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cat`** — Displaying the contents of a file.
* **`./`** — Specifying a file in the current directory.
* **Special filenames** — A filename such as `-` can have a special meaning in Linux commands.
* **Standard input (`stdin`)** — `-` is used by Linux commands to represent input from the terminal.
