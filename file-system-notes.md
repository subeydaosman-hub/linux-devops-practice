# Linux File System Notes

## 1. pwd

The pwd command shows the current directory I am working in.

Example:
pwd
## 2. mkdir

The mkdir command creates a new directory (folder).

Example:
mkdir projects
## 3. touch

The touch command creates an empty file if it doesn't already exist.

Example:
touch practice.txt
## 4. cp

The cp command copies a file while keeping the original.

Example:
cp practice.txt backup.txt
## 5. less

The less command opens a file in a scrollable viewer, allowing me to read it at my own pace.

Example:
less /etc/services

## Linux Permissions and Ownership

The chmod command changes file permissions.

Example:
chmod 644 permissions-practice.txt

644 means:
- Owner: read and write
- Group: read only
- Others: read only

The chown command changes file ownership.

Example:
sudo chown root:root hello.sh

This changes both the owner and group of hello.sh to root.

Press q to exit the viewer.