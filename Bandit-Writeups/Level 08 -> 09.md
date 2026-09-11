# 🎯Bandit — Level 8 → Level 9

##  Objective

The goal of this level is to find the password for the next level. The password is a unique line that appears only once in the file `data.txt`.

##  Commands Used

| **Command** | **Meaning**                   |
| ----------- | ----------------------------- |
| `ssh`       | Connect to a remote server    |
| `ls`        | List files and directories    |
| `sort`      | Sort lines of text            |
| `uniq`      | Find or remove repeated lines |
| `exit`      | Exit the current session      |

##  Solution

### Step 1️: Connect to the Bandit Level 8 Server

After completing Level 7, I connected to the Bandit Level 8 account using SSH on port 2220.

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

When askeed for the password, I entered the password obtained in Level 7 and was connected to the Bandit Level 8 server.

------------------

### Step 2: List the Files

I checked the files available using:

```bash
ls
```

The output showed:

```text
data.txt
```

This showed that there is a file named `data.txt`.

-------

### Step 3: Find the Unique Line

The file ha many lines. Since int is mentioned that the password is a unique line, I used the following commmand.

```bash
sort data.txt | uniq -u
```

###  Command Explanation

* `sort data.txt` → Sorts all the lines in `data.txt`.
* `|` → Sends the output of the first command to the next command.
* `uniq -u` → Displays only the lines that occur once

The command displayed the **PASSWORD** for Level 9.

--------

### Step 4: Exit and Log in to Level 9

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 9 account:

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

When askeed for the password, I entered the password obtained earlier and was connected to the Level 9 server.

##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files in a directory.
* **`sort`** — Sorting lines of text.
* **`uniq`** — Finding or removing duplicate lines.
* **`uniq -u`** — Displaying only unique lines.
* **Pipe (`|`)** — Passing the output of one command as input to another command.
* Using `sort` before `uniq` to correctly identify duplicate and unique lines.
