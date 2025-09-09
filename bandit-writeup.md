# 🐧 OverTheWire Bandit Write-Up (Levels 0 → 5)
## 🔹 Level 0 → 1

**Challenge Description:**  
Connect to the remote Bandit server using SSH with the provided credentials.

**Provided Info:**  
- Host: `bandit.labs.overthewire.org`  
- Port: `2220`  
- Username: `bandit0`  
- Password: `bandit0`

**Solution Overview:**  
Use `ssh` (Secure Shell) to log in remotely. Successful connection gives us access to Level 0’s environment.

**Tools Used:**  
- `ssh`

**Command:**  

ssh bandit0@bandit.labs.overthewire.org -p 2220

## 🔹 Level 1 → 2

**Challenge Description:**  
The password for Level 2 is stored in a file named `-`.

**Provided Info:**  
- Filename: `-` (special case since `-` often means stdin)

**Solution Overview:**  
Since `-` conflicts with stdin usage, we explicitly specify the path as `./-` to treat it as a normal file.

**Tools Used:**  
- `cat` (display file content)

**Command:**  

cat ./-

## 🔹 Level 2 → 3

**Challenge Description:**  
The password for the next level is in a file called `spaces in this filename`.

**Provided Info:**  
- File name includes spaces.

**Solution Overview:**  
Spaces in filenames must be handled by wrapping the name in quotes or escaping them with backslashes.

**Tools Used:**  
- `cat`

**Command:**  

cat "spaces in this filename"

## 🔹 Level 3 → 4

**Challenge Description:**  
The password for the next level is stored in a hidden file inside the `inhere` directory.

**Provided Info:**  
- Directory: `inhere`  
- Hidden files start with `.` in Linux.

**Solution Overview:**  
Navigate into the `inhere` directory, list hidden files using `ls -a`, then read the hidden file.

**Tools Used:**  
- `ls -a`  
- `cat`

**Commands:**  

cd inhere
ls -a
cat .hidden

## 🔹 Level 4 → 5

**Challenge Description:**  
The password is stored in the only human-readable file in the `inhere` directory.

**Provided Info:**  
- Directory: `inhere` contains multiple files.  
- Only one file is ASCII text.

**Solution Overview:**  
Use the `file` command to determine the type of each file in the directory. The ASCII text file is the one containing the password. Once identified, display its contents with `cat`.

**Tools Used:**  
- `file`  
- `cat`

**Commands:**  

cd inhere
file ./*
cat ./-file07
