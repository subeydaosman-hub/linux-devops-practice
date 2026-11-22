# Task 4: Linux Process Management

## Commands Practised

- `ps aux` — Lists running processes and their details.
- `ps aux | grep nginx` — Searches for processes related to nginx.
- `top` — Displays live system processes and resource usage.
- `htop` — Provides an interactive view of processes, CPU and memory usage.
- `sleep 600 &` — Starts a test process in the background.
- `jobs` — Lists background jobs managed by the current shell.
- `fg %1` — Brings job 1 into the foreground.
- `ps -p 18649 -o pid,comm` — Finds a specific process using its PID.
- `kill 18649` — Sends a termination signal to that process.
- `killall sleep` — Terminates processes named sleep.

## Practical Exercise

I started a background process with `sleep 600 &` and received PID 18649.

I used `ps -p 18649 -o pid,comm` to confirm it was running, then `kill 18649` to terminate it.

I verified the process had stopped using `ps -p 18649`.

I also started two sleep processes and successfully terminated both using `killall sleep`.

## Key Learning

A PID identifies a specific process. `kill` targets a PID, while `killall` targets processes by name.
