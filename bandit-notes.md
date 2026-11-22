# OverTheWire Bandit: Linux Challenges (Levels 0–20)

## Overview

As part of my DevOps bootcamp, I completed OverTheWire Bandit Levels 0–20 to strengthen my Linux command-line and troubleshooting skills.

These challenges helped me practise file navigation, permissions, text processing, compression, SSH authentication, networking, and secure communication.

## Challenge Walkthrough

### Level 0 → 1: Connecting via SSH

**Challenge:** Connect to the Bandit server and retrieve the first password.

**Commands:**
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

**What I learned:** How to connect to a remote Linux server using SSH, list files, and read file contents.

### Level 1 → 2: Special Filenames

**Challenge:** Read a file named `-`.

**Command:**
```bash
cat ./-
```

**What I learned:** Using `./` allows Linux to interpret a filename beginning with `-` as a file rather than a command option.

### Level 2 → 3: Filenames Containing Spaces

**Challenge:** Read a filename containing spaces.

**Command:**
```bash
cat "./--spaces in this filename--"
```

**What I learned:** Quotation marks allow commands to handle filenames containing spaces.

### Level 3 → 4: Hidden Files

**Challenge:** Find a hidden file inside the `inhere` directory.

**Commands:**
```bash
ls -la inhere
cat inhere/...Hiding-From-You
```

**What I learned:** `ls -la` reveals hidden files, which usually begin with a dot.

### Level 4 → 5: Identifying File Types

**Challenge:** Find the only human-readable file among several files.

**Commands:**
```bash
file inhere/*
cat inhere/-file07
```

**What I learned:** `file` identifies file types, while `cat` displays their contents.

### Level 5 → 6: Finding Files by Size

**Challenge:** Locate a human-readable file with specific properties.

**Commands:**
```bash
find inhere -type f -size 1033c
file inhere/maybehere07/.file2
```

**What I learned:** `find` searches files by criteria such as size and type. The `c` suffix specifies bytes.

### Level 6 → 7: Searching by Ownership

**Challenge:** Find a file owned by a specific user and group, with a particular size.

**Command:**
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

**What I learned:** How to search the filesystem using ownership and size filters, and redirect error messages with `2>/dev/null`.

### Level 7 → 8: Searching Text

**Challenge:** Find a password associated with the word `millionth`.

**Command:**
```bash
grep "millionth" data.txt
```

**What I learned:** `grep` searches for matching text within files.

### Level 8 → 9: Finding Unique Lines

**Challenge:** Identify the only line that occurs once.

**Command:**
```bash
sort data.txt | uniq -u
```

**What I learned:** Pipes connect commands. Sorting groups identical lines so `uniq -u` can identify the unique entry.

### Level 9 → 10: Extracting Readable Strings

**Challenge:** Find readable text hidden inside a file containing binary data.

**Command:**
```bash
strings data.txt
```

**What I learned:** `strings` extracts readable character sequences from binary files.

### Level 10 → 11: Base64 Decoding

**Challenge:** Decode Base64-encoded text.

**Command:**
```bash
base64 -d data.txt
```

**What I learned:** Base64 is an encoding format, not encryption.

### Level 11 → 12: ROT13

**Challenge:** Decode text encrypted using a ROT13 letter substitution.

**Command:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

**What I learned:** `tr` translates characters, and ROT13 replaces letters with those 13 positions away in the alphabet.

### Level 12 → 13: Multiple Compression Layers

**Challenge:** Recover a password hidden inside a hexadecimal dump of repeatedly compressed and archived data.

**Key commands:**
```bash
xxd -r data.txt > /tmp/bandit12-work/data.bin
file /tmp/bandit12-work/data.bin
gzip -dc input.bin > output.bin
bzip2 -dc input.bin > output.bin
tar -xf archive.bin -C /tmp/bandit12-work/
```

**What I learned:** How to reverse a hexadecimal dump, identify compression formats, decompress gzip and bzip2 files, and extract tar archives.

The main troubleshooting approach was to identify each file type before deciding which command to use.

### Level 13 → 14: SSH Private Key Authentication

**Challenge:** Access another Bandit account using a provided SSH private key.

**Key commands:**
```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private ~/Linux/
chmod 600 ~/Linux/sshkey.private
ssh -i ~/Linux/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

**What I learned:** How to transfer files securely using `scp`, restrict private key permissions, and authenticate using `ssh -i`.

### Level 14 → 15: Network Communication with Netcat

**Challenge:** Submit a password to a service listening on port 30000.

**Command:**
```bash
nc localhost 30000
```

**What I learned:** `nc` (Netcat) establishes network connections and allows data to be sent to a listening service.

### Level 15 → 16: Encrypted Network Communication

**Challenge:** Submit a password through an SSL/TLS-encrypted connection.

**Command:**
```bash
openssl s_client -connect localhost:30001 -quiet
```

**What I learned:** How to establish a TLS connection using OpenSSL and communicate securely with a network service.

### Level 16 → 17: Port Scanning and SSH Keys

**Challenge:** Identify the correct service among several open ports and retrieve an SSH private key.

**Commands:**
```bash
nmap -p 31000-32000 localhost
nmap -sV -p 31046,31518,31691,31790,31960 localhost
openssl s_client -connect localhost:31790 -quiet
```

**What I learned:** How to scan ports with Nmap, identify running services, distinguish encrypted services from ordinary TCP services, and use an SSH private key for authentication.

### Level 17 → 18: Comparing Files

**Challenge:** Identify the changed password between two files.

**Command:**
```bash
diff passwords.old passwords.new
```

**What I learned:** `diff` compares files and displays their differences, which is useful when reviewing configuration changes.

### Level 18 → 19: Executing Remote Commands

**Challenge:** Read a file on a server that immediately terminates interactive SSH sessions.

**Command:**
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

**What I learned:** SSH can execute a remote command directly without opening an interactive shell.

### Level 19 → 20: Setuid Executables

**Challenge:** Use a special executable to read a file requiring another user's permissions.

**Command:**
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

**What I learned:** Setuid executables can run with the permissions of their owner, illustrating how Linux handles privileged execution.

## Key Skills Developed

- Linux navigation and file management
- File permissions and ownership
- Searching and processing text
- Pipes and output redirection
- File compression and archive extraction
- SSH authentication and secure file transfers
- Network ports and service identification
- TLS-encrypted communication
- Troubleshooting and command-line problem-solving

## Reflection

Completing these challenges helped me become more comfortable working in a Linux terminal. Some tasks required multiple attempts, particularly those involving nested compression formats and SSH authentication.

My biggest takeaway was the importance of understanding error messages, identifying the problem before selecting a command, and solving technical challenges systematically.

These skills provide a foundation for my continued learning in DevOps, containers, automation, and cloud infrastructure.

---

**Security note:** Passwords and private SSH keys have intentionally been excluded from this documentation.