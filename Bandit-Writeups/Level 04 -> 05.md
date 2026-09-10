# 🎯Bandit — Level 4 → Level 5

##  Objective

The goal of this level is to find the password for the next level. The password is stored in the **only human-readable file** inside the `inhere` directory.

There are multiple files in the directory, so we need to identify which file contains readable text.

##  Commands Used

| Command | Meaning                     |
| ------- | --------------------------- |
| `ssh`   | Connect to a remote server  |
| `ls`    | List files and directories  |
| `cd`    | Change directory            |
| `file`  | Identify the type of a file |
| `cat`   | Display file contents       |
| `exit`  | Exit the current session    |

##  Solution

### Step 1️: Connect to the Bandit Level 4 Server

After completing Level 3, I connected to the Bandit Level 4 account using SSH on port 2220.

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained in Level 3.

The login was successful, and I was connected to the Bandit Level 4 server.

### Step 2: List the Files

I checked the files available in the current directory using:

```bash
ls
```

The output showed:

```text
inhere
```

This means there is a directory named `inhere` in the current directory.

### Step 3: Enter the `inhere` Directory

I used the `cd` command to enter the `inhere` directory:

```bash
cd inhere
```

After entering the directory, I listed the files using:

```bash
ls
```

The directory contained multiple files.

Since the objective says that only one of these files is **human-readable**, I needed to identify the type of each file.

### Step 4: Identify the Human-Readable File

I used the `file` command to check the type of all the files:

```bash
file ./*
```

The command displayed information about each file.

Most of the files were identified as **data** or non-readable files, while one file was identified as **ASCII text**.

The human-readable file was:

```text
--file07
```


### Step 5: Read the File and Obtain the Password

I used the `cat` command to display the contents of the file:

```bash
cat ./--file07
```

Using `./` specifies that `--file07` is a file in the current directory.

The command displayed the **PASSWORD** required to log in to Bandit Level 5.

I copied the password for the next login.

### Step 6: Exit and Log in to Level 5

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 5 account:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from the human-readable file.

The login was successful, and I was now connected to the Bandit Level 5 server.

##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`cd`** — Moving between directories.
* **`file`** — Identifying the type and format of files.
* **Human-readable files** — Files containing readable text such as ASCII text.
* **`./`** — Specifying a file in the current directory.
* **`cat`** — Displaying the contents of a file.
