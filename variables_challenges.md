# PWN College - Linux Luminarium: Shell Variables Challenges

## Challenge 1: Printing Variables

The flag has been put into the variable called "FLAG". Use echo to print it out and solve the challenge.

### Solution:

- to access variables we can use $ symbol

Use this blob for pasting commands you've run:
```sh
$ $FLAG
```

### Flag: 

```
pwn.college{4bEZxrvmCdCck9Tz42l_1W0BHGV.QX3UTN0wiN1EzNzEzW}
```

### Notes:
- Use `echo $VARIABLE_NAME` to print variable values
- The `$` symbol triggers variable expansion
- Example: `echo $PWD` prints the current working directory
- Variable names are case-sensitive

---

## Challenge 2: Setting Variables

Set the PWN variable to the value COLLEGE to solve this challenge.

### Solution:

- for assigning values = without spaces is used

Use this blob for pasting commands you've run:
```sh
$ PWN=COLLEGE 
```

### Flag: 

```
pwn.college{cawLlO4uAozeE7kxO3jFak-wm0k.QX5UTN0wiN1EzNzEzW}
```

### Notes:
- Use `VARIABLE=value` to set variables (no spaces around `=`)
- Don't use `$` when setting variables, only when accessing them
- Both variable names and values are case-sensitive
- Wrong: `VAR = 1337` (spaces cause errors)
- Correct: `VAR=1337`

---

## Challenge 3: Multi-word Variables

Set the variable PWN to the value "COLLEGE YEAH" (with a space) to solve this challenge.

### Solution:

- for multi word assigning we have to use quotes 

Use this blob for pasting commands you've run:
```sh
$ PWN="COLLEGE YEAH"
$ 
```

### Flag: 

```
pwn.college{AgU6Tm8foNyHiJIt7J8290hyI5P.QXwYTN0wiN1EzNzEzW}
```

### Notes:
- Use quotes to set variables with spaces: `VAR="value with spaces"`
- Without quotes, the shell interprets spaces as command separators
- Both single `'` and double `"` quotes work for this purpose
- Example: `PWN="COLLEGE YEAH"`

---

## Challenge 4: Exporting Variables

Invoke /challenge/run with the PWN variable exported and set to COLLEGE, and the COLLEGE variable set to PWN but not exported.

### Solution:

- exported PWN=COLLEGE
- set value of COLLEGE=PWN and did not export

Use this blob for pasting commands you've run:
```sh
$ export PWN=COLLEGE
$ COLLEGE=PWN
$ /challenge/run
```

### Flag: 

```
pwn.college{4eVwKBjOuroDZHLm-D50vysxdKZ.QXyYTN0wiN1EzNzEzW}
```

### Notes:
- Use `export VAR=value` to make variables available to child processes
- Variables without export are local to the current shell
- Method 1: `VAR=value` then `export VAR`
- Method 2: `export VAR=value` (combined)
- Child processes only see exported variables

---

## Challenge 5: Printing Exported Variables

Learn about viewing exported environment variables using the env command.

### Solution:

- env is used to access all the exported variables
- 
- 

Use this blob for pasting commands you've run:
```sh
$ env
```

### Flag: 

```
pwn.college{grWHU8ImxioeY_Jl7ZRTG7dFjFv.QX4UTN0wiN1EzNzEzW}
```

### Notes:
- Use `env` to list all exported environment variables
- Use `env | grep PATTERN` to search for specific variables
- Environment variables are inherited by child processes
- `printenv` is another command that does the same thing

---

## Challenge 6: Storing Command Output

Read the output of /challenge/run directly into a variable called PWN using command substitution.

### Solution:
- $(blah) is used to access a command and use it as a variable

Use this blob for pasting commands you've run:
```sh
$ PWN=$(/challenge/run)
$ 
```

### Flag: 

```
pwn.college{coqxwoLoWUmV2ykE0MJDb5j51wF.QX1cDN1wiN1EzNzEzW}
```

### Notes:
- Use `VAR=$(command)` for command substitution
- Alternative older syntax: `VAR=`command`` (backticks)
- The command's output is stored in the variable
- Example: `FLAG=$(cat /flag)`
- Prefer `$()` over backticks for readability and nesting

---

## Challenge 7: Reading Input

Use the `read` command to read user input into a variable.

### Solution:
- to take input read command is used

Use this blob for pasting commands you've run:
```sh
$ read PWN
COLLEGE
```

### Flag: 

```
pwn.college{orQ4GKtp0fOjggLnCL7u25bITRs.QX4cTN0wiN1EzNzEzW}
```

### Notes:
- Use `read VAR` to read from stdin into a variable
- `read` waits for user input and stores it in the variable
- Press Enter to submit the input
- Multiple variables: `read VAR1 VAR2` splits input by spaces

---

## Challenge 8: Reading Files

Read the contents of /challenge/read_me into the PWN environment variable using input redirection with read.

### Solution:

- to read files we can use < with read

Use this blob for pasting commands you've run:
```sh
$ read PWN < /challenge/read_me
```

### Flag: 

```
pwn.college{8S_Q3_dQ5-I50ok9jooqJ8ceTEC.QXwIDO0wiN1EzNzEzW}
```

### Notes:
- Use `read VAR < file` to read file contents into a variable
- This redirects file as stdin to the read command
- More efficient than `VAR=$(cat file)`
- Example: `read PWN < /challenge/read_me`
- The file content goes directly into the variable

---

## References:

- [PWN College - Linux Luminarium Variables](https://pwn.college/linux-luminarium/variables/)
- [Bash Manual - Shell Variables](https://www.gnu.org/software/bash/manual/html_node/Shell-Variables.html)
- [Bash Manual - Command Substitution](https://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html)
- [Advanced Bash-Scripting Guide - Variables](https://tldp.org/LDP/abs/html/variables.html)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- Variables store data in shell sessions
- `VARIABLE=value` sets variables (no spaces around `=`)
- `$VARIABLE` accesses variable values (variable expansion)
- Quotes `"value"` allow spaces in variable values
- `export` makes variables available to child processes
- `$(command)` captures command output into variables
- `read VAR` reads user input into variables
- `read VAR < file` reads file contents into variables
- Variable names and values are case-sensitive

### Common Mistakes:
- Adding spaces around `=` when setting variables
- Forgetting `$` when accessing variables
- Using `$` when setting variables (wrong: `$VAR=value`)
- Not using quotes for multi-word values
- Forgetting to export variables for child processes
- Confusing local variables with environment variables

### Alternative Methods:
- `export VAR=value` vs `VAR=value; export VAR`
- `$(command)` vs backticks for command substitution
- `read VAR < file` vs `VAR=$(cat file)`
- `env` vs `printenv` for viewing environment variables
