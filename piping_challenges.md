# PWN College - Linux Luminarium: Piping Challenges

## Challenge 1: Redirecting output

Use output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- used comparision symbol to redirect pwn to college

Use this blob for pasting commands you've run:
```sh
$ echo PWN > COLLEGE
$ 
```

### Flag: 

```
pwn.college{oy8wimfA8--UweM0vO5liQ7UJVP.QX0YTN0wiN1EzNzEzW}
```

### Notes:
- Use `>` to redirect output to a file
- `echo PWN > COLLEGE` writes PWN to file COLLEGE
- The `>` operator creates or overwrites the target file

---

## Challenge 2: Redirecting more output

Practice more complex output redirection scenarios with different commands and files.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- used > to redirect output

```sh
$ /challenge/run > myflag
$ cat myflag
```

### Flag: 

```
 pwn.college{YwMaw1mYm18-yDYi81USkavncWj.QX1YTN0wiN1EzNzEzW}
```

### Notes:
- Any command's output can be redirected with `>`
- Be careful not to overwrite important files

---

## Challenge 3: Appending output

Learn to append output to files instead of overwriting them using the append operator.

### Solution:

- used >> to append and not overwrite/replace

```sh
$ /challenge/run >> /home/hacker/the-flag
$ cat /home/hacker/the-flag
```

### Flag: 

```
pwn.college{4ylJ8UiYvWj2lpZ_KyxOXLKbaQL.QX3ATO0wiN1EzNzEzW}
```

### Notes:
- Use `>>` to append to files instead of overwriting
- `>>` adds content to the end of existing files
- If file doesn't exist, `>>` creates it like `>`

---

## Challenge 4: Redirecting errors

Practice redirecting stderr (standard error) to files using error redirection.

### Solution:

-  '>' is used for stdout (std. output) and '2>' is used for stderr (std. error)

Use this blob for pasting commands you've run:
```sh
$ /challenge/run > myflag 2> instructions
$ cat myflag
```

### Flag: 

```
pwn.college{4JJ0oSHXHqwwXFoZfBtQWk9j4xE.QX3YTN0wiN1EzNzEzW}
```

### Notes:
- Use `2>` to redirect stderr (file descriptor 2)
- `2>>` appends stderr to files
- `2>&1` redirects stderr to wherever stdout is going

---

## Challenge 5: Redirecting input

Use input redirection to provide file contents as input to commands via stdin.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- '<' is used for directing files into a file

Use this blob for pasting commands you've run:
```sh
$ echo COLLEGE > PWN
$ /challenge/run < PWN
```

### Flag: 

```
pwn.college{MOr3GA4iwX2I_YKnYX2UUqYAKOF.QXwcTN0wiN1EzNzEzW}
```

### Notes:
- Use `<` to redirect file contents as input to commands
- `command < file` feeds file contents to command via stdin
- Equivalent to `cat file | command` in many cases

---

## Challenge 6: Grepping stored results

Combine output redirection with grep to search through saved command outputs.

### Solution:
- redirected /challenge/run to /tmp/data.txt and used grep to search for flag

Use this blob for pasting commands you've run:
```sh
$ /challenge/flag >> /tmp/data.txt
$ grep pwn /tmp/data.txt
```

### Flag: 

```
pwn.college{c3TjFJGrZnmKYmhzNP5V0gZptEM.QX4EDO0wiN1EzNzEzW}
```

### Notes:
- First redirect command output to file, then grep the file
- Or use pipes: `command | grep pattern`
- Redirection is useful when you need to save intermediate results

---

## Challenge 7: Grepping live output

Use pipes to search through command output in real-time without saving to files.

### Solution:

- used pipe '|' operator to directly grep the flag 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run | grep pwn.college
$ 
```

### Flag: 

```
pwn.college{cUuHrvgwhVJabt6kC7W0nghFqLh.QX5EDO0wiN1EzNzEzW}
```

### Notes:
- Use `|` to pipe output directly to grep
- `command | grep pattern` searches output without saving
- Pipes connect stdout of first command to stdin of second

---

## Challenge 8: Grepping errors

Learn to grep through stderr output using error redirection and pipes.

### Solution:
- >& is used to redirect one file descriptor to another so i used 2>& 1 ie error to output

Use this blob for pasting commands you've run:
```sh
$ /challenge/run 2>& 1 | grep pwn.college
$ 
```

### Flag: 

```
pwn.college{Es1iRnu3Iv7DYpmPrkaOizjc8F6.QX1ATO0wiN1EzNzEzW}
```

### Notes:
- Use `2>&1` to combine stderr with stdout, then pipe
- `command 2>&1 | grep pattern` searches both output streams
- Or redirect stderr to file first, then grep the file

---

## Challenge 9: Filtering with grep -v

Use grep's invert match option to filter out unwanted lines from output.

### Solution:
- used grep -v to filter out all that contain DECOY
- 
- 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run | grep -v DECOY
$ 
```

### Flag: 

```
pwn.college{EHkHUDpo_jUzyx1I48fwFzawIcq.0FOxEzNxwiN1EzNzEzW}
```

### Notes:
- `grep -v pattern` shows lines that DON'T match the pattern
- Useful for filtering out unwanted content
- Can be combined with pipes and redirection

---

## Challenge 10: Duplicating piped data with tee

Use the `tee` command to both save output to a file and pass it through a pipe.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ 
$ 
```

### Flag: 

```
pwn.college{ }
```

### Notes:
- `tee` writes input to both a file and stdout
- `command | tee file | next_command` saves and continues pipeline
- Use `tee -a` to append to file instead of overwrite

---

## Challenge 11: Process substitution for input

Learn to use process substitution to provide command output as input files.

### Solution:

- used <(/path) for using commands as diff

Use this blob for pasting commands you've run:
```sh
$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
$ 
```

### Flag: 

```
pwn.college{Ynf8c9M4lnccmdHUFry_6fpDv6W.0lNwMDOxwiN1EzNzEzW}
```

### Notes:
- Use `<(command)` for process substitution as input
- Creates a temporary file-like object from command output
- Useful when commands expect file arguments, not stdin

---

## Challenge 12: Writing to multiple programs

Practice using pipes and process substitution to send output to multiple programs.

### Solution:
- sent output of /challenge/hack as input of both /challenge/the and /challenge/planet

Use this blob for pasting commands you've run:
```sh
$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
$ 
```

### Flag: 

```
pwn.college{U1_GfdD5QFjSUbjn38XOMy6FgrT.QXwgDN1wiN1EzNzEzW}
```

### Notes:
- Use `tee` with process substitution: `command | tee >(prog1) >(prog2)`
- Process substitution `>()` creates temporary pipes for output
- Enables splitting output to multiple destinations

---

## Challenge 13: Split-piping stderr and stdout

Learn to handle stdout and stderr separately in complex pipelines.

### Solution:

- 2> for stderr and >() for using file as command
- | for piping

Use this blob for pasting commands you've run:
```sh
$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
$ 
```

### Flag: 

```
pwn.college{ozy60fJOTG4g5paUVONyk1vFQdF.QXxQDM2wiN1EzNzEzW}
```

### Notes:
- Use file descriptors and redirection to split streams
- `command 2> >(stderr_handler) | stdout_handler`
- Process substitution `>()` creates temporary pipes for different streams

---

## Challenge 14: Named pipes

Work with named pipes (FIFOs) to create persistent communication channels between processes.

### Solution:
- made a fifo using mkfifo and piped the output of /challenge/run to it 
- in a new terminal and read out the fifo file.

Use this blob for pasting commands you've run:
```sh
$ mkfifo /tmp/flag_fifo
$ /challenge/run > /tmp/flag_fifo
$ cat /tmp/flag_fifo
```

### Flag: 

```
pwn.college{Um663oPSVG_3RvkhF1ndRBTTtGX.01MzMDOxwiN1EzNzEzW}
```

### Notes:
- Use `mkfifo` to create named pipes
- Named pipes persist in the filesystem until deleted
- Enable communication between unrelated processes
- One process writes to pipe, another reads from it

---

## References:

- [PWN College - Linux Luminarium Piping](https://pwn.college/linux-luminarium/piping/)
- [Bash Manual - Redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)
- [Advanced Bash-Scripting Guide - I/O Redirection](https://tldp.org/LDP/abs/html/io-redirection.html)
- [Linux mkfifo Manual](https://man7.org/linux/man-pages/man1/mkfifo.1.html)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- `>` redirects stdout to file (overwrites)
- `>>` redirects stdout to file (appends)  
- `<` redirects file contents to stdin
- `2>` redirects stderr to file
- `2>&1` redirects stderr to stdout
- `|` pipes stdout of one command to stdin of another
- `tee` duplicates input to both file and stdout
- `grep -v` inverts matches (shows non-matching lines)
- `<(command)` process substitution for input
- `>(command)` process substitution for output
- `mkfifo` creates named pipes (FIFOs)
- File descriptors: 0=stdin, 1=stdout, 2=stderr

### Common Mistakes:
- Forgetting that `>` overwrites files completely
- Not distinguishing between stdout and stderr
- Confusing `<` and `>` directions
- Forgetting to use `2>&1` when you need both output streams
- Not understanding when to use process substitution vs regular pipes

### Alternative Methods:
- Using `cat file | command` instead of `command < file`
- Using temporary files vs pipes for complex operations
- Process substitution vs named pipes for inter-process communication
- Different approaches to splitting and merging I/O streams
