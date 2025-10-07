
# PWN College - Linux Luminarium: Processes and Jobs Challenges

This document follows the same format as the provided *globbing* example and summarizes the **Processes and Jobs** module from pwn.college. For each challenge I include: a short description, placeholder sections for solutions and commands, a placeholder for the flag, and brief notes/tips.

---

## Challenge 1: Listing Processes

**Description:** Learn to list running processes using `ps` (`ps -ef`, `ps aux`, etc.). In this level, `/challenge/run` has been renamed and `/challenge` is not listable; find the running filename via the process list and execute it.

### Solution:

- used -efww as command to find what files are running

### Commands:

```sh
$ -ps -efww
$ /challenge/9132-run-5395
```

### Flag:

```
pwn.college{I_U9yrzWAoEa4KCLi9WMk9-Wd-h.QX4MDO0wiN1EzNzEzW}
```

### Notes:
- `ps -ef` and `ps aux` show similar information; use the `ww` option to avoid truncation of the command column.
- Look for processes whose command line contains `/challenge` or suspicious names.

---

## Challenge 2: Killing Processes

**Description:** Use `kill` to terminate a running process. `/challenge/run` will refuse to run while `/challenge/dont_run` is running; find and kill `dont_run`.

### Solution:
- used ps -efww to find the pid of /challenge/dont_run and killed it.

### Commands:

```sh
$ ps -efww
$ kill 136
$ /challenge/run
```

### Flag:

```
pwn.college{czVSlvuA9-M4pvLzKQpwxtSNwBB.QXyQDO0wiN1EzNzEzW}
```

### Notes:
- `kill` with no signal sends SIGTERM; if that fails, `kill -9 <PID>` sends SIGKILL (use carefully).
- Make sure you targeted the correct PID.

---

## Challenge 3: Interrupting Processes

**Description:** Learn to interrupt a foreground process using Ctrl-C. `/challenge/run` will refuse to give the flag until you interrupt it.

### Solution:

- interrupted /challenge/run using ^C.

### Commands:

```sh
$ /challenge/run
(ctrl)+C
```

### Flag:

```
pwn.college{ozermEjf0cnzwhL81uQQ5HXUSWE.QXzQDO0wiN1EzNzEzW}
```

### Notes:
- Ctrl-C sends SIGINT to the foreground process.
- Some programs install custom handlers for SIGINT; behavior may vary.

---

## Challenge 4: Killing Misbehaving Processes

**Description:** A decoy process is hogging a named pipe (`/tmp/flag_fifo`) that `/challenge/run` wants to write into. Find and kill the decoy process (likely `/challenge/decoy`) so the flag can be written to the FIFO.

### Solution:

- killed decoy process

### Commands:

```sh
$ ps -efww
$ kill 151
$ /challenge/run
#new terminal
$ cat /tmp/flag_fifo
```

### Flag:

```
pwn.college{Yp5mfIIZb_llPO6-T6U6AYtpbCv.0FNzMDOxwiN1EzNzEzW}
```

### Notes:
- Pipes are buffered: you may see decoy output after killing the process for a brief moment.
- `lsof` (if present) can show which process has the FIFO open.

---

## Challenge 5: Suspending Processes

**Description:** Learn to suspend a foreground job with `Ctrl-Z`. This level asks you to launch a copy of `run`, suspend it, then launch another copy while the first remains suspended.

### Solution:
 - suspended process using ctrl + z
### Commands:

```sh
$ /challenge/run 
^Z
$ /challenge/run
```

### Flag:

```
pwn.college{Q5e4D5bcP2LxQyWypLatiWZ3qKa.QX1QDO0wiN1EzNzEzW}
```

### Notes:
- `jobs` lists suspended/backgrounded jobs.
- The `T` state in `ps` indicates a suspended process.

---

## Challenge 6: Resuming Processes

**Description:** Resume suspended jobs using `fg`. This level requires you to suspend `run` and then resume it.

### Solution:

- used fg to resume suspended tasks.

### Commands:

```sh
$ /challenge/run
^Z
$ fg /challenge/run
```

### Flag:

```
pwn.college{QhFBCXD9vjK5btpuyWZRjgA_NCm.QX2QDO0wiN1EzNzEzW}
```

### Notes:
- `fg` returns a job to the foreground; `%1` references job number 1 as shown by `jobs`.

---

## Challenge 7: Backgrounding Processes

**Description:** Background a process with `bg` (or launch it with `&`). This level asks you to have another copy of `run` running in the background while you run a foreground copy.

### Solution:

- used bg to send /challenge/run in background

### Commands:

```sh
$ /challenge/run
^Z
$ bg /challenge/run
$ /challenge/run

```

### Flag:

```
pwn.college{QCBqH_ZEh2Wo2ivqTip_QLSsgp0.QX3QDO0wiN1EzNzEzW}
```

### Notes:
- Background jobs continue to run but do not occupy the terminal.
- Use `ps -o user,pid,stat,cmd` to inspect job states (`T` for stopped, `S` for sleeping/background).

---

## Challenge 8: Foregrounding Processes

**Description:** Bring a backgrounded process to the foreground with `fg`.

### Solution:

- first suspended then ran in background, then brought to foreground.

### Commands:

```sh
$ /challenge/run
^Z
$ bg /challenge/run
$ fg /challenge/run
```

### Flag:

```
pwn.college{8FrLjQ2gT6U-uTkZYsALMB-ltPo.QX4QDO0wiN1EzNzEzW}
```

### Notes:
- Foregrounding a job will give it the terminal's input and signals.

---

## Challenge 9: Starting Backgrounded Processes

**Description:** Start a process already backgrounded by appending `&` to the command.

### Solution:

- used & for running in background

### Commands:

```sh
4 /challenge/run &
```

### Flag:

```
pwn.college{IMtEyQrHd9zvzhyky_q4RSoud_H.QX5QDO0wiN1EzNzEzW}
```

### Notes:
- Backgrounded processes are convenient when you want long-running tasks to continue while you use the shell.

---

## Challenge 10: Process Exit Codes

**Description:** Commands exit with codes. Retrieve the exit code returned by `/challenge/get-code` (via `$?`) and then pass it to `/challenge/submit-code`.

### Solution:
- used $? to get the error value

### Commands:

```sh
$ /challenge/get-code
$ echo $?
$ /challenge/submit-code 224
```

### Flag:

```
pwn.college{o1ple_yqFrf686ylih9zfqiKNGQ.QX5YDO1wiN1EzNzEzW}
```

### Notes:
- Successful commands usually return `0`, errors return non-zero.
- Capture `$?` immediately after the command finishes.

---

## References

- PWN College Processes and Jobs module: https://pwn.college/linux-luminarium/processes/
- Bash manual (job control and signals): https://www.gnu.org/software/bash/manual/
