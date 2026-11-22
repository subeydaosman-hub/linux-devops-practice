# Task 5: Linux Text Processing

## Commands Practised

### 1. grep — Search for Text

`grep "root" /etc/passwd`
- Searches for lines containing "root".

`grep -i "ROOT" /etc/passwd`
- Searches without distinguishing uppercase and lowercase letters.

`grep -r "TODO" ~/Linux/`
- Searches recursively for TODO in files within my Linux workspace.

### 2. Pipes and wc — Count Matches

`grep -i "root" /etc/passwd | wc -l`
- Uses a pipe to pass grep results to wc.
- `wc -l` counts the matching lines.
- My result was 1.

### 3. awk — Extract Information

`ps aux | awk '{print $1, $11}'`
- Displays process owners and command fields.

`awk -F: '{print $1, $6}' /etc/passwd`
- Uses a colon as the field separator.
- Displays usernames and home directories.

### 4. sed — Replace or Display Text

`echo "I am learning Linux" | sed 's/Linux/DevOps/'`
- Replaces the first occurrence of Linux with DevOps.

`echo "Linux is fun. I love Linux." | sed 's/Linux/DevOps/g'`
- Replaces every occurrence of Linux on the line.
- The `g` flag means global.

`sed -n '10,20p' /etc/passwd`
- Displays lines 10 through 20, inclusive.

## Assignment Challenge: Find Bash Users

Command:

`awk -F: '$7 == "/bin/bash" {print $1}' /etc/passwd`

My output:

root
subeyda

Explanation:
- `$7` represents the login shell.
- The condition checks for `/bin/bash`.
- `$1` prints the username.
- I found two matching accounts.

## Key Learning

- grep searches for matching text.
- awk filters and extracts fields.
- sed transforms text and selects lines.
- Pipes (`|`) connect commands by passing output from one command to another.
