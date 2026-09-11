# 🎯Bandit — Level 12 → Level 13

## Objective

The password for the next level is stored in `data.txt`, which is a hexdump of a file that has been compressed multiple times.

We have to reverse the hexdump and repeatedly decompress or extract the file until we find the password.

## Commands Used

| **Command** | **Meaning**                         |
| ----------- | ----------------------------------- |
| `ssh`       | Connect to the Bandit remote server |
| `mktemp -d` | Create a temporary directory        |
| `cp`        | Copy a file                         |
| `cd`        | Change the current directory        |
| `xxd -r`    | Reverse a hexdump into binary data  |
| `file`      | Identify the type of a file         |
| `mv`        | Rename a file                       |
| `gzip -d`   | Decompress a gzip file              |
| `bzip2 -d`  | Decompress a bzip2 file             |
| `tar -xf`   | Extract a tar archive               |
| `cat`       | Display the contents of a file      |
| `rm`        | Remove a file                       |
| `exit`      | Exit the SSH session                |

## Solution

### Step 1️: Connect to the Bandit Level 12 Server

First, connect to the Bandit Level 12 server using SSH.

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

When asked for password, I entered the password that was obtained from Level 11.

---

### Step 2: Create a Temporary Directory

Create a temporary directory to work with the compressed files.

```bash
mktemp -d
```

Example output:

```text
/tmp/tmp.abc123
```

This creates a temporary directory where we can safely modify and extract the files.

---

### Step 3: Copy `data.txt` to the Temporary Directory

Copy the `data.txt` file into the temporary directory.

```bash
cp data.txt /tmp/tmp.abc123
```

Now move into the directory:

```bash
cd /tmp/tmp.abc123
```

---

### Step 4: Reverse the Hexdump

The `data.txt` file contains hexadecimal data. We need to convert this hexdump back into its original binary form.

```bash
xxd -r data.txt > data
```

###  Command Explanation

* `xxd` → Used to create or process hexadecimal representations of files.
* `-r` → Reverses the hexadecimal dump back into binary data.
* `data.txt` → The hexdump file.
* `>` → Redirects the output into a file.
* `data` → The reconstructed binary file.

Now identify the file type:

```bash
file data
```

The output tells us which compression format is being used.

---

### Step 5: Decompress the Gzip File

The first file is identified as a gzip compressed file.

Rename it with the `.gz` extension:

```bash
mv data data.gz
```

Then decompress it:

```bash
gzip -d data.gz
```

Check the resulting file:

```bash
file data
```

The file is now identified as **bzip2 compressed data**.

---

### Step 6: Decompress the Bzip2 File

Rename the file with the `.bz2` extension:

```bash
mv data data.bz2
```

Then decompress it:

```bash
bzip2 -d data.bz2
```

Check the file again:

```bash
file data
```

The next layer is again a gzip compressed file.

Rename and decompress it:

```bash
mv data data.gz
gzip -d data.gz
```

Then check again:

```bash
file data
```

---

### Step 7: Extract the Tar Archive

Since the file is now identified as a **POSIX tar archive**.

Extract it using:

```bash
tar -xf data
```

Check the files:

```bash
ls
```

A new file such as `data5.bin` will appear.

Check its type:

```bash
file data5.bin
```

If it is another tar archive, extract it:

```bash
tar -xf data5.bin
```

Another file will appear. Continue checking each file using:

```bash
file <filename>
```

---

### Step 8: Continue Decompressing the Remaining Layers

In this level, the compression formats are layered.

For example, when `data6.bin` is identified as bzip2:

```bash
mv data6.bin data.bz2
bzip2 -d data.bz2
```

Then check:

```bash
file data
```

If it is a tar archive:

```bash
tar -xf data
```

After extraction, check the newly created file.

When the final file is identified as gzip:

```bash
mv data8.bin data.gz
gzip -d data.gz
```

Check the result:

```bash
file data
```

The final output is:

```text
data: ASCII text
```

This means the file now contains readable text.

###  Important

After every decompression or extraction, use:

```bash
file data
```

The `file` command tells us the current file type, which helps us decide which command to use next.

Decompress/Extract until the file becomes ACII text.

The general process is:

```text
file → identify format → decompress/extract → file → repeat
```

---

### Step 9: Read the Password

Once the file becomes ASCII text, display its contents:

```bash
cat data
```

This is the **PASSWORD** for Level 13.

---

### Step 10: Exit and Log in to Level 13

After obtaining the password, exit the current session:

```bash
exit
```

Then connect to Level 13:

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

When asked for password, I entered the password obtained earlier and was now connected to Level 13.

## Concepts Learned

* **Hexdump** — A hexadecimal representation of binary data.
* **`xxd -r`** — Converts a hexdump back into binary data.
* **`file`** — Identifies the type and format of a file.
* **Gzip** — A compression format that can be decompressed using `gzip -d`.
* **Bzip2** — A compression format that can be decompressed using `bzip2 -d`.
* **Tar** — An archive format that can be extracted using `tar -xf`.
* **Layered compression** — A file can be compressed multiple times using different formats.
* **Temporary directories** — `mktemp -d` provides a temporary workspace for processing files.
