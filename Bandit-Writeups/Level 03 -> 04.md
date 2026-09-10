# 🎯Bandit — Level 3 → Level 4

##  Objective

The goal of this level is to find the password for the next level. The password is stored in a **hidden file** inside the `inhere` directory.

##  Commands Used

| Command  |  Meaning                                 |
| -------- | --------------------------------------  |
| `ssh`    | Connects to a remote server             |
| `ls`     | Lists files and directories             |
| `cd`     | Changes directory                       |
| `ls -a`  | Lists all files, including hidden files |
| `cat`    | Displays the file contents              |
| `exit`   | Exits the current session               |

##  Solution

### Step 1️: Connect to the Bandit Level 3 Server

After completing Level 2, I connected to the Bandit Level 3 account using SSH on port 2220.

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier in Level 2 and was connected to the Bandit Level 3 server.

----------

### Step 2: List the Files

I checked the files available using:
```bash
ls
```

The output showed:

```text
inhere
```

This means there is a directory named `inhere` in the current directory.

----------

### Step 3: Enter the `inhere` Directory

I used the `cd` command to enter the `inhere` directory:

```bash
cd inhere
```

Since the objective says that the password is stored in a **hidden file**, Using the following command:

```bash
ls -a
```

It showed all the files including a hidden file which was:


```text
...Hiding-From-You
```

----------

### Step 4: Read the Hidden File

I used the `cat` command to display the contents of the hidden file:

```bash
cat ...Hiding-From-You
```

The command displayed the **PASSWORD** required to log in to Bandit Level 4.

I copied the password for the next login.

----------

### Step 6: Exit and Log in to Level 4

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 4 account:

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

When asked for the password, I entered the password obtained earlier from Level 3 and was connected to the Bandit Level 4 server.


##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cd`** — Moving between directories.
* **`ls -a`** — Listing all files, including hidden files.
* **Hidden file** — Files beginning with `.` are hidden in Linux.
* **`cat`** — Displaying the contents of a file.
