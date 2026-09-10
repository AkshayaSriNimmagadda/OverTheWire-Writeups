# Bandit — Level 6 → Level 7

## 🎯 Objective

The goal of this level is to find the password for the next level. The password is stored **somewhere on the server**.

The required file has these properties:

* Owned by user `bandit7`
* Owned by group `bandit6`
* Exactly 33 bytes in size

## 🛠️ Commands Used

| **Command** | **Meaning**                      |
| ----------- | -------------------------------- |
| `ssh`       | Connect to a remote server       |
| `find`      | Search for files and directories |
| `cat`       | Display file contents            |
| `exit`      | Exit the current session         |

## 🔍 Solution

### Step 1️: Connect to the Bandit Level 6 Server

After completing Level 5, I connected to the Bandit Level 6 account using SSH on port 2220.

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained in Level 5.

The login was successful, and I was connected to the Bandit Level 6 server.

### Step 2: Search for the Required File

The objective says that the file is located **somewhere on the server**, so I started the search from the root directory `/`.

I used the following command:

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### 📖 Command Explanation

* `find` → Searches for files and directories.
* `/` → Starts the search from the **root directory**, so the entire server filesystem is searched.
* `-user bandit7` → Finds files owned by the user `bandit7`.
* `-group bandit6` → Finds files belonging to the group `bandit6`.
* `-size 33c` → Finds files that are exactly **33 bytes** in size. Here, `c` means bytes.
* `2>/dev/null` → Hides error messages such as **Permission denied** while searching directories that we cannot access.


The command returned the path of the file that matched all the required conditions.

### Step 3: Read the File and Obtain the Password

After finding the required file, I used the `cat` command to display its contents.

```bash
cat /var/lib/dpkg/info/bandit7.password
```

The command displayed the **PASSWORD** required to log in to Bandit Level 7.

I copied the password for the next login.

### Step 4: Exit and Log in to Level 7

After obtaining the password, I exited the current SSH session:

```bash
exit
```

Then, I connected to the Bandit Level 7 account:

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

When prompted for the password, I entered the password obtained from the required file.

The login was successful, and I was now connected to the Bandit Level 7 server.

## 🧠 Concepts Learned

* **SSH** — Connecting to a remote server.
* **`find`** — Searching for files based on specific conditions.
* **`/`** — The root directory of the Linux filesystem.
* **`-user`** — Searching for files owned by a specific user.
* **`-group`** — Searching for files belonging to a specific group.
* **`-size 33c`** — Searching for a file that is exactly 33 bytes.
* **`2>/dev/null`** — Hiding unwanted error messages.
* **`cat`** — Displaying the contents of a file.
