
## 1 — Chaining with Semicolons

**Description:** Use `;` to run commands sequentially. For this level you must run `/challenge/pwn` and then `/challenge/college`, chaining them with a semicolon.

### Solution:

- chained with a semicolon

### Commands:

```sh
$ /challenge/pwn;/challenge/college
```

### Flag:

```
pwn.college{8qs9RIeT6BHIjyHfYekRdZy4ZEY.QX1UDO0wiN1EzNzEzW}
```

### Notes:
- Semicolons run commands sequentially regardless of exit code.

---

## 2 — Building on Success (&&)

**Description:** Use `&&` to run a second command only if the first succeeds. Chain `/challenge/first-success` and `/challenge/second` using `&&` to obtain the flag.

### Solution:

- used && to chain

### Commands:

```sh
$ /challenge/first-success && /challenge/second
```

### Flag:

```
pwn.college{c0Ip0ZGz6IXW8vPImNz-YYUnlE5.0lM0MDOxwiN1EzNzEzW}
```

### Notes:
- `&&` runs the second command only if the first exits with status `0`.

---

## 3 — Handling Failure (||)

**Description:** Use `||` to run a second command only if the first fails. Chain `/challenge/first-failure` and `/challenge/second` using `||`.

### Solution:

- used || to chain based on failures 

### Commands:

```sh
$ /challenge/first-failure || /challenge/second
```

### Flag:

```
pwn.college{oDWH2FqYUAOwHltLhOsc1M7onxh.01M0MDOxwiN1EzNzEzW}
```

### Notes:
- `||` runs the second command only if the first exits with non-zero status.

---

## 4 — FIRST SHELL SCRIPTS

**Description:** using shell scripts 

### Solution:

made a script 

### Commands:

```sh
# cat > x.sh << 'end'
>/challenge/pwn
> /challenge/college
> end
$ bash x.sh
```

### Flag:

```
pwn.college{oFVS3XXKIgyTej9zff8Q2dRmCT0.QXxcDO0wiN1EzNzEzW}
```

### Notes:
- scripts run like semicolon

---
## 5 — Piping (|)

**Description:** Use `|` to connect the stdout of one command to the stdin of another. Chain two commands such that the output of one is processed by the next to reveal the flag.

### Solution:
created a script then piped the output

### Commands:

```sh
$ cat > sc.sh << "end"
> /challenge/pwn
> /challenge/college
> end
$ bash sc.sh | /challenge/solve
```

### Flag:

```
pwn.college{s5gQfPXrCX7mNyhfsfmHxfI7r2v.QX4ETO0wiN1EzNzEzW}
```

### Notes:
- Pipes create a unidirectional data stream connecting processes.
---
## 6 — Executable Shell Scripts

**Description:** Make a shell script executable and run it directly (without invoking `bash`). Create a script to invoke `/challenge/solve`, make it executable, and run it by path.

### Solution:

- made a script and then gave permission to the script to run as an executable

### Commands:

```sh
$ cat < script.sh >> "end"
> /challenge/solve
> end
$ chmod +x script.sh 
$ ./script.sh
```

### Flag:

```
pwn.college{gOPdj-g0Dc_LnBE9GYI4HNH6y0f.QX0cjM1wiN1EzNzEzW}
```

### Notes:
- Mark a script executable with `chmod a+x script.sh`, then run with `./script.sh`.
---

## 7 — Understanding Shebangs

**Description:** Add a proper shebang (`#!`) as the first line of your script so it can be executed portably by the kernel. Create `/home/hacker/solve.sh` with a shebang and output "hack the planet".

### Solution:
- shebang is used for interpreter programs

### Commands:

```sh
$ cat > /home/hacker/solve.sh <<'EOF'
 > #!/bin/bash
> echo "hack the planet"
> EOF
$ chmod +x ./solve.sh
$ ./solve.sh
$ /challenge/run
```

### Flag:

```
pwn.college{4R-k6gQ8mybM0yd-g4ExayXkRKc.0VOzMDOxwiN1EzNzEzW}
```

### Notes:
- The shebang must be the very first line of the file (no leading blank lines).

---

## 8 — Scripting with Arguments

**Description:** Make scripts accept command-line arguments and use `$1`, `$2`, etc. to access them. Follow the challenge prompt on the site for exact requirements.

### Solution:

- used $2 $1 to make arguements reverse

### Commands:

```sh
$ cat > ./solve.sh << 'end'
#!/bin/bash
echo "$2 $1"
end
$ chmod +x ./solve.sh
$ ./solve.sh
$/challenge/run
```

### Flag:

```
pwn.college{QwEixjW3K7bg5RN_-tkIml63WJU.0VNzMDOxwiN1EzNzEzW}
```

### Notes:
- `$1` is the first argument, `$2` is the second, etc.

---


## 9 — Conditioning

**Description:** conditionals like if and fi are used to check for conditions

### Solution:

made a script with if statement

### Commands:

```sh
$ echo '#!/bin/bash
if [ "$1" = "pwn" ]; then
    echo "college"
fi
' > /home/hacker/solve.sh
$ chmod +x /home/hacker/solve.sh
$ ./solve.sh
$ /challenge/run
```

### Flag:

```
pwn.college{ghWrWH9LEqXRo-toC7O-ywDXYrY.0lNzMDOxwiN1EzNzEzW}
```

---

### 10 - else
**Description:** - Your if statements so far have handled specific cases, but what about everything else? That's where else comes in!

### Solution:

added else to the if already used.

### Commands:

```sh
$ echo '#!/bin/bash
# Checks if the first argument ($1) is "pwn" and outputs "college" if true.

if [ "$1" = "pwn" ]; then
    echo "college"
fi
' > /home/hacker/solve.sh
$ chmod +x ./solve.sh
$ /challenge/run
```

### Flag:

```
# pwn.college{s7XK4mqD3Cy3CmbhxwNHOifKoDs.01NzMDOxwiN1EzNzEzW}
```

### Notes:
- use else for everything else

---

## 11 — multiple conditions

**Description:** You've learned how to use a single if statement to check a condition. But what if you need to check multiple conditions? You can use elif (short for else if):

### Solution:

multiple if then elif used

### Commands:

```sh
$ echo '#!/bin/bash
if [ "$1" = "hack" ]; then
    echo "the planet"
elif [ "$1" = "pwn" ]; then
    echo "college"
elif [ "$1" = "learn" ]; then
    echo "linux"
else
    echo "unknown"
fi' > /home/hacker/solve.sh
$ chmod +x ./solve.sh
$ /challenge/run
```

### Flag:

```
pwn.college{c-F90sx-PTupiSdcuhZAk2aalPM.0FOzMDOxwiN1EzNzEzW}
```

### Notes:
- multiple conditions we can use elif.

---

## 12 — Reading SCRIPTS

**Description:** we will learn to read shell scripts. /challenge/run is a shell script that requires you to put in a secret password, but that password is hardcoded into the script iself! Read the script (using, say, cat), figure out the password, and get the flag!

### Solution:
used cat to read the script

### Commands:

```sh
$ cat /challenge/run 
$ /challenge/run
hack the PLANET
```

### Flag:

```
# pwn.college{8DpFnFdqmRabk8FZMcxQq_t7yMQ.0lMwgDOxwiN1EzNzEzW}
```

### Notes:
- cat can be used for reading shell scripts aswell

---
## References

- Original module: PWN College — Chaining Commands. See the interactive challenges on the website for live terminals and exact requirements.
