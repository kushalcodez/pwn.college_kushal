# PWN College - Linux Luminarium: Globbing Challenges

## Challenge 1: Matching with *

Change your directory to /challenge using globbing to keep the argument you pass to cd to at most four characters, then run /challenge/run for the flag.

### Solution:
- cd into /challenge by using the wildcard

Use this blob for pasting commands you've run:
```sh
$ cd /ch* 
$ /challenge/run
```

### Flag: 

```
pwn.college{csgmhQDhImIPavJH9RLjgJIw-T6.QXxIDO0wiN1EzNzEzW}
```

### Notes:
- The * wildcard can match zero or more characters
- Remember that globbing happens before the command executes

---

## Challenge 2: Matching with ?

Change your directory to /challenge using the ? character instead of c and l in the argument to cd, then run /challenge/run for the flag.

### Solution:
- used ? in place of c and ?? in place of ll

Use this blob for pasting commands you've run:
```sh
$ cd /?ha??enge 
$ /challenge/run
```

### Flag: 

```
pwn.college{8hFVSswA5xAwwMYLbHDvIl_RewF.QXyIDO0wiN1EzNzEzW}
```

### Notes:
- The ? matches exactly one character, no more, no less
- Each ? represents one specific character position

---

## Challenge 3: Matching with []

Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

### Solution:
- accessed /challenge/files using cd and then used ls to know what files are present
- used square bracket as an argument to run the files file_b,file_a,file_s,file_h

Use this blob for pasting commands you've run:
```sh
$ cd /challenge/files
$ ls
$ challenge/run file_[bash]
```

### Flag: 

```
pwn.college{0-w8v-sb11pwtoLuxioYbHOx53a.QXzIDO0wiN1EzNzEzW}
```

### Notes:
- Square brackets match any ONE character from the set inside
- Solution: `file_[bash]` to match file_b, file_a, file_s, file_h
- Order inside brackets doesn't matter for matching

---

## Challenge 4: Matching paths with []

Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- ran challenge/run with an argument of an absolute path

Use this blob for pasting commands you've run:
```sh
$ /challenge/run /challenge/files/file_[bash]
```

### Flag: 

```
pwn.college{EyKOetROIHaf5sRTm0a7sGEg25c.QX0IDO0wiN1EzNzEzW}
```

### Notes:
- Need to use absolute paths starting with /
- Solution: `/challenge/files/file_[bash]`
- Don't forget to include the full path in your glob

---

## Challenge 5: Mixing globs

Change to /challenge/files and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

### Solution:
- cd'd the /challenge/files directory then ran an argument with /challenge/run as given in the question

Use this blob for pasting commands you've run:
```sh
$ cd /challenge/files
$ /challenge/run *p*
```

### Flag: 

```
pwn.college{YqPagCUGCatrMbn7d3fwPQO2mKd.0lM3kjNxwiN1EzNzEzW}
```

### Notes:
- Need exactly 2 asterisks in a 3-character-or-less pattern
- Solution: `*p*` matches any file containing 'p'
- The * can match zero characters, so this covers all cases with 'p'

---

## Challenge 6: MIXING GLOBS

Go to /challenge/files and, using globbing, write a single, short (6 characters or less) glob that will match the files "challenging", "educational", and "pwning" when passed as an argument to /challenge/run.

### Solution:
- first accessed the /challenge/files directory then checked all the files in it using ls command then first tried using *n argument but it didnt work,
after that tried using the first letters of all the required return files and then used [cep]*.


Use this blob for pasting commands you've run:
```sh
$ cd /challenge/files
$ ls 
$ /challenge/run [cep]*
```

### Flag: 

```
pwn.college{06YktZ7zPBJ6T0g3XHnSslAFpP8.QX1IDO0wiN1EzNzEzW}
```

### Notes:
- Need to find a pattern that matches "challenging", "educational", "pwning"
- Look for common characters or patterns across all three words
- Solution might be `*n*` (all contain 'n') or similar pattern (mistake)
- Must be 6 characters or less

---

## Challenge 7: Exclusion with !

Go to /challenge/files and run /challenge/run with all files that don't start with p, w, or n using the ! exclusion operator.

### Solution:

- used a globbing argument which returns all the files that dont start with p,w,n by using ! in [] and ending with a *

Use this blob for pasting commands you've run:
```sh
$ cd /challenge/files
$ /challenge/run [!pwn]*
```

### Flag: 

```
pwn.college{sN5Xznim9410GPvIRG8blzkHuMs.QX2IDO0wiN1EzNzEzW}
```

### Notes:
- The ! character inverts the bracket match (exclusion)
- Solution: `[!pwn]*` matches files that DON'T start with p, w, or n
- In newer bash, ^ can be used instead of ! for negation
- Be careful: ! has special meaning outside of brackets
- forgot using * after `[!pwn]` and got an error
---

## Challenge 8: Tab completion

The flag has been copied to /challenge/pwncollege, but you must use tab completion to specify the filename (you cannot type it manually).

### Solution:

- used tab key to autocomplete

Use this blob for pasting commands you've run:
```sh
$ /challenge/pwn<tab>
```

### Flag: 

```
pwn.college{0sepHKGi7CcTSetXuqt0yPECD2Y.0FN0EzNxwiN1EzNzEzW}
```

### Notes:
- Must use tab completion - typing the filename manually won't work
- Start typing `/challenge/pwn` then press TAB
- The system forces you to use autocomplete for learning purposes
- Tab completion prevents typos and saves time

---

## Challenge 9: Tab completion with multiple options

Navigate to /challenge/files and use tab completion to find and read the flag file that starts with pwncollege.

### Solution:
- used two tabs to find out all the files that have the common prefix

Use this blob for pasting commands you've run:
```sh
$ cat /challenge/files/pwncollege<tab>
$ cat /challenge/files/pwncollege-<tab><tab>
$ cat /challenge/files/pwncollege-flag
```

### Flag: 

```
pwn.college{MAU8xAxYOSBOGkLdr8pIxY2rO7q.0lN0EzNxwiN1EzNzEzW}
```

### Notes:
- Multiple files start with "pwncollege" - tab twice to see options
- First TAB completes common prefix, second TAB shows all options
- Navigate through options or continue typing to narrow down
- Look for the file that contains the flag

---

## Challenge 10: Tab completion for commands

Find and execute the command that starts with "pwncollege" using tab completion to get the flag.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- autocomplete can be also used on commands 

Use this blob for pasting commands you've run:
```sh
$ pwncollege <tab>
```

### Flag: 

```
pwn.college{08e9PLUc6Hfrj_sns2y-AX0PiE0.0VN0EzNxwiN1EzNzEzW}
```

### Notes:
- Tab completion works for commands, not just files
- Start typing `pwncollege` and press TAB to autocomplete
- The command will execute and give you the flag
- Be careful with command autocompletion - verify before running

---

## References:

- [PWN College - Linux Luminarium Globbing](https://pwn.college/linux-luminarium/globbing/)
- [Bash Manual - Pattern Matching](https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- * wildcard matches any number of characters
- ? wildcard matches exactly one character  
- [] bracket expressions match any character within the brackets
- ! or ^ at the start of [] negates the match
- Tab completion helps avoid typing errors and discover files/commands
- Globbing happens before command execution
- Be careful with globs to avoid unintended file matches

### Common Mistakes:
- forgot * many times 
- silly mistakes that could be improved easily
