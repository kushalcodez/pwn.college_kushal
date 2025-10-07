# PWN College - Linux Luminarium: Data Manipulation Challenges

## Challenge 1: Translating characters

Use the `tr` command to translate characters. The /challenge/run will print the flag but will swap the casing of all characters (A becomes a and vice-versa). Undo it with tr to get the flag.

### Solution:

- used tr to shift casing of characters in flag 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run | tr 'a-z A-Z' 'A-Z a-z'
```

### Flag: 

```
pwn.college{cRdZTJ7xG1LLBOs5Kggd2rHoGaF.01MxEzNxwiN1EzNzEzW}
```

### Notes:
- `tr` translates characters from stdin to stdout
- Basic usage: `echo OWN | tr O P` outputs "PWN"
- Multiple characters: `echo PWM.COLLAGE | tr MA NE` outputs "PWN.COLLEGE"
- For case swapping: `tr 'A-Z' 'a-z'` converts uppercase to lowercase
- Reverse: `tr 'a-z' 'A-Z'` converts lowercase to uppercase
- To swap both: `tr 'A-Za-z' 'a-zA-Z'`

---

## Challenge 2: Deleting characters

Use `tr` with the `-d` flag to delete specific characters from input.

### Solution:
- used tr -d to delete characters from flag
- 
- 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run | tr -d '^,%'
```

### Flag: 

```
pwn.college{cvIRr5xcRWci_bDF-fc01quLjUr.0FNxEzNxwiN1EzNzEzW}
```

### Notes:
- `tr -d` deletes specified characters
- Example: `echo "hello123" | tr -d '0-9'` removes all digits
- Can delete multiple characters: `tr -d 'aeiou'` removes vowels
- Useful for cleaning up data

---

## Challenge 3: Deleting newlines

Delete newlines from the flag output using `tr -d` with the escaped newline specification `\n`.

### Solution:

- used \n to delete newline 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run | tr -d "\n"
```

### Flag: 

```
pwn.college{EbyS4C7qvLwA-E5Ak72qQTT0l7N.0VNxEzNxwiN1EzNzEzW}
```

### Notes:
- Use `tr -d "\n"` to delete newlines
- The backslash `\` escapes the newline character
- Must use quotes: `"\n"` so shell doesn't interpret it
- Converts multi-line output to single line
- Fun fact: To delete backslash itself, use `\\`

---

## Challenge 4: Extracting the first lines with head

Use `head` to grab the first 7 lines from /challenge/pwn and pipe them to /challenge/college. Build a composite command with two pipes connecting three commands.

### Solution:

- used 2 pipes and 3 commands to get the flag

Use this blob for pasting commands you've run:
```sh
$ /challenge/pwn | head -n 7 | /challenge/run 
```

### Flag: 

```
pwn.college{kPqjselcz0HfbvUi8qiwmNtJMgX.0lNxEzNxwiN1EzNzEzW}
```

### Notes:
- `head` displays first few lines of input
- Default: shows first 10 lines
- `head -n N` shows first N lines
- Example: `head -n 7` shows first 7 lines
- Solution pattern: `command1 | head -n 7 | command2`
- Useful for previewing large files or limiting output

---

## Challenge 5: Extracting specific sections of text

Use `cut` to extract specific columns from the output. The /challenge/run outputs lines with random numbers and flag characters as columns. Extract the flag characters using cut, then join them with `tr -d "\n"`.

### Solution:
- first checked /challenge/run to know which column has the flag value
- used cut arguement and tr to delete new lines

Use this blob for pasting commands you've run:
```sh
$ /challenge/run
$ /challenge/run | cut -d ' ' -f 2 | tr -d '\n'
```

### Flag: 

```
pwn.college{cbe2Q7qIt-Ds7XxDDftudLYo56Q.01NxEzNxwiN1EzNzEzW}
```

### Notes:
- `cut` extracts columns/fields from text
- `-d` specifies delimiter (e.g., `-d ' '` for space)
- `-f` specifies field number (e.g., `-f 2` for second column)
- Example: `echo "a b c" | cut -d ' ' -f 2` outputs "b"
- Solution pattern: `/challenge/run | cut -d ' ' -f N | tr -d "\n"`
- Delimiter must be in quotes if it's a special character

---

## Challenge 6: Sorting data

Use `sort` to organize data alphabetically. Find the real flag in /challenge/flags.txt among 100 fake flags. When sorted alphabetically, the real flag will be at the end.

### Solution:
- used -r to find the reverse order of flags when sorted
- 
- 

Use this blob for pasting commands you've run:
```sh
$ sort -r /challenge/flags.txt
```

### Flag: 

```
pwn.college{4tpNRs_T7A91WC6J42bi_z3rNWx.0FM0MDOxwiN1EzNzEzW}
```

### Notes:
- `sort` orders lines alphabetically by default
- Useful flags:
  - `-r` : reverse order (Z to A)
  - `-n` : numeric sort (for numbers)
  - `-u` : unique lines only (remove duplicates)
  - `-R` : random order
- Example: `sort file.txt` sorts lines A to Z
- To get last line after sorting: `sort file | tail -n 1`
- Or reverse sort and get first: `sort -r file | head -n 1`

---

## References:

- [PWN College - Linux Luminarium Data](https://pwn.college/linux-luminarium/data/)
- [tr Manual](https://man7.org/linux/man-pages/man1/tr.1.html)
- [head Manual](https://man7.org/linux/man-pages/man1/head.1.html)
- [cut Manual](https://man7.org/linux/man-pages/man1/cut.1.html)
- [sort Manual](https://man7.org/linux/man-pages/man1/sort.1.html)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- `tr` translates or deletes characters from input
- `tr 'SET1' 'SET2'` replaces characters in SET1 with SET2
- `tr -d 'SET'` deletes characters in SET
- `head -n N` shows first N lines of input
- `cut -d 'DELIM' -f N` extracts Nth field using delimiter
- `sort` orders lines alphabetically
- Escaped characters like `\n` represent special characters
- Pipe multiple commands together for complex data processing

### Common Mistakes:
- Forgetting quotes around special characters in tr
- Not escaping newlines: use `"\n"` not just `\n`
- Confusing field numbers in cut (they start at 1, not 0)
- Forgetting to specify delimiter with `-d` in cut
- Not using `-n` flag with head when you need specific line count
- Using numeric sort when alphabetic is needed (or vice versa)

### Alternative Methods:
- `tail -n +N` to skip first N-1 lines instead of head
- `awk` as alternative to cut for field extraction
- `sed` for more complex character manipulation
- Combining sort with `tail -n 1` or `head -n 1` to get extreme values
- Using `uniq` after sort to remove duplicates
