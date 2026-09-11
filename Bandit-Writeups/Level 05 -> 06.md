# 🎯Bandit — Level 5 → Level 6

##  Objective

The goal of this level is to find the password for the next level. The password is obtained using following properties:

* Human-readable
* Exactly 1033 bytes in size
* Not executable

##  Commands Used

| **Command** | **Meaning**                                   |
| ----------- | --------------------------------------------- |
| `ssh`       | Connect to a remote server                    |
| `ls`        | List files and directories                    |
| `cd`        | Change directory                              |
| `find`      | Search for files based on specific conditions |
| `cat`       | Display file contents                         |
| `exit`      | Exit the current session                      |

##  Solution

### Step 1️: Connect to the Bandit Level 5 Server

After completing Level 4, I connected to the Bandit Level 5 account using SSH on port 2220.

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

When askeed for the password, I entered the password obtained in Level 4 and was connected to the Bandit Level 5 server.

-----

### Step 2: List the Files

I checked the files available in the current directory using:

```bash
ls
```

The output showed:

```text
inhere
```

This showed that there is a directory named `inhere` in the current directory.

--------------------------

### Step 3: Enter the `inhere` Directory

I used the `cd` command to enter the `inhere` directory:

```bash
cd inhere
```

After entering the directory, I checked the contents using:

```bash
ls
```

The directory contained several subdirectories and files.

----

### Step 4: Find the Required File

I used the `find` command to search for the file that would match all the properties mentioned above:

```bash
find . -type f -size 1033c ! -executable
```

###  Command Explanation

* `find` → Searches for files and directories.
* `.` → Starts the search from the current directory.
* `-type f` → Searches only for regular files.
* `-size 1033c` → Searches for files that are exactly 1033 bytes. Here, `c` means bytes.
* `! -executable` → Excludes files that are executable.
  
----

### Step 5: Read the File and Obtain the Password

The command returned a file that matched all the required properties. Then, I used the `cat` command to display its contents:

```bash
cat ./maybehere07/.file2
```

The command displayed the **PASSWORD** for Bandit Level 6.

-----

### Step 6: Exit and Log in to Level 6

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 6 account:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```
When askeed for the password, I entered the password obtained in Level 5 and was connected to the Bandit Level 6 server.

##  Concepts Learned

* **SSH** — Connecting to a remote server.
* **`ls`** — Listing files and directories.
* **`cd`** — Moving between directories.
* **`find`** — Searching for files based on conditions.
* **`-type f`** — Searching only for regular files.
* **`-size 1033c`** — Finding a file that is exactly 1033 bytes.
* **`! -executable`** — Finding a file that is not executable.
* **`cat`** — Displaying the contents of a file.

