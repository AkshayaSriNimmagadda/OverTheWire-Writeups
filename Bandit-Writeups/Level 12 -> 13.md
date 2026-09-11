# 🎯Bandit — Level 12 → Level 13

## Objective

The password for the next level is stored in `data.txt`, which is a hexdump of a file that has been compressed multiple times.

Our task is to reverse the hexdump and repeatedly decompress the file until we find the password.

## Commands Used

| **Command** | **Meaning** |
| --- | --- |
| `ssh` | Connect to the Bandit remote server |
| `mktemp -d` | Create a temporary directory |
| `cp` | Copy a file |
| `cd` | Change the current directory |
| `head` | Display the beginning of a file |
| `xxd -r` | Reverse a hexdump into binary data |
| `file` | Identify the type of a file |
| `mv` | Rename a file |
| `gzip -d` | Decompress a gzip file |
| `bzip2 -d` | Decompress a bzip2 file |
| `tar -xf` | Extract a tar archive |
| `cat` | Display the contents of a file |
| `exit` | Exit the SSH session |

## Solution

### Step 1️: Connect to the Bandit Level 12 Server

First, connect to the Bandit Level 12 server using SSH.

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
``````

----

### Step 2: Create a Temporary Directory

Create a temporary directory to work with the compressed files.

mktemp -d

Example output:

/tmp/tmp.abc123

This creates a temporary directory where we can safely modify and extract the files.

-----

### Step 3: Copy data.txt to the Temporary Directory

Copy the data.txt file into the temporary directory.

cp data.txt /tmp/tmp.abc123

Replace /tmp/tmp.abc123 with the directory created by your mktemp -d command.

Now move into the directory:

```cd /tmp/tmp.abc123```

------

### Step 4: Check the Contents of data.txt

Use head to view the beginning of the file.

head data.txt

The output contains hexadecimal values instead of normal readable text.

This shows that data.txt is a hexdump.

--------

### Step 5: Reverse the Hexdump

Convert the hexdump back into its original binary form using xxd.

````xxd -r data.txt data````

 Command Explanation
xxd → Used to create or process hexadecimal representations of files.
-r → Reverses the hexadecimal dump back into binary data.
data.txt → The hexdump file.
data → The reconstructed binary file.

Now check the type of the file:

file data

The output will tell us which compression format is being used.

For example:

data: gzip compressed data
Step 6: Decompress the File

If file data shows that it is a gzip compressed file, rename it with the .gz extension:

mv data data.gz

Then decompress it:

gzip -d data.gz

Now check the resulting file again:

file data

The file may now be another type of compressed file.

Step 7: Continue Decompressing

The file is compressed multiple times, so we need to repeat the process.

If the file is bzip2 compressed data:

mv data data.bz2
bzip2 -d data.bz2

Then check again:

file data

If the file is a tar archive:

mv data data.tar
tar -xf data.tar

Then check the extracted file:

file data

Continue identifying and extracting the file until it becomes readable text.

 Important

After every extraction, use:

file data

The file command tells us what type of file we have and therefore which command should be used next.

Step 8: Read the Password

After repeatedly decompressing and extracting the file, the final file will contain readable text.

Use:

cat data

The output is the password for Level 13.

Step 9: Exit and Log in to Level 13

After obtaining the password, exit the current session:

exit

Then connect to Level 13:

ssh bandit13@bandit.labs.overthewire.org -p 2220

Enter the password obtained from Level 12.

Concepts Learned
Hexdump — A hexadecimal representation of binary data.
xxd -r — Converts a hexdump back into binary data.
file — Identifies the type and format of a file.
gzip — Used to compress and decompress files.
bzip2 — Another compression format and decompression tool.
tar — Used to create and extract archives.
mktemp -d — Creates a temporary directory.
Repeated compression — A file can be compressed multiple times using different compression formats.
