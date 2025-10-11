# PWN College - Linux Luminarium: Perceiving Permissions Challenges

## Challenge 1: Changing File Ownership

Learn to use the `chown` command to change file ownership and access files owned by different users.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- changed owner of /flag using `chown` command

Use this blob for pasting commands you've run:
```sh
$ chown hacker /flag
$ cat /flag
```

### Flag: 

```
pwn.college{Ul_fTlTrBh7XlenDjwTb7N5ZF38.QXxEjN0wiN1EzNzEzW}
```

### Notes:
- `chown user file` changes file owner to specified user
- `chown user:group file` changes both owner and group
- Requires root/sudo privileges to change ownership
- Syntax: `chown [owner][:group] file`
- Example: `chown hacker flag.txt`
- Use `ls -l` to verify ownership changes

---

## Challenge 2: Groups and Files

Learn about group ownership and how to use the `chgrp` command to change group ownership.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- used `chgrp` to change owner group of /flag to hacker(user)'s group
- 
- 

Use this blob for pasting commands you've run:
```sh
$ chgrp hacker /flag
$ cat /flag
```

### Flag: 

```
pwn.college{ksLEBklmTVQ97x6CKjP8aqmSZ7C.QXxcjM1wiN1EzNzEzW}
```

### Notes:
- `chgrp group file` changes file's group ownership
- Files have both user owner and group owner
- Groups allow multiple users to share access
- Check groups with `groups` or `id` command
- `ls -l` shows both user and group: `user group`
- Example: `chgrp hackers file.txt`

---

## Challenge 3: Fun With Groups Names

Practice working with groups that have unusual or complex names.

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
pwn.college{sKRVDnlcN0JkJkW-1_pPtbU99dm.QXzcjM1wiN1EzNzEzW}
```

### Notes:
- Group names can contain special characters
- Use quotes if group name has spaces
- `id` command shows all groups you belong to
- Primary group vs supplementary groups
- `/etc/group` file lists all system groups

---

## Challenge 4: Changing Permissions

Learn to use `chmod` to modify file permissions (read, write, execute).

### Solution:

- added readable permission for all users
- 
- 

Use this blob for pasting commands you've run:
```sh
$ ls -l /flag
$ chmod a+r /flag
$ cat /flag
```

### Flag: 

```
pwn.college{sKRVDnlcN0JkJkW-1_pPtbU99dm.QXzcjM1wiN1EzNzEzW}
```

### Notes:
- `chmod` changes file permissions (mode)
- Three permission types: read (r), write (w), execute (x)
- Three permission sets: user (u), group (g), others (o)
- Symbolic: `chmod u+x file` adds execute for user
- Symbolic: `chmod go-w file` removes write for group and others
- View permissions with `ls -l`

---

## Challenge 5: Executable Files

Learn about execute permissions and how they affect files and directories.

### Solution:

- used chmod to change permissions
- 
- 

Use this blob for pasting commands you've run:
```sh
$ ls -l /challenge/run
$ chmod g+x,u+x,o+x /challenge/run
$ /challenge/run
```

### Flag: 

```
pwn.college{knqGFeB4aCPc8Ojubs1XSfFw1_E.QXyEjN0wiN1EzNzEzW}
```

### Notes:
- Execute (x) permission allows running files as programs
- For directories, execute allows entering (cd) into them
- `chmod +x file` makes file executable
- Scripts need both read and execute permissions
- Check with `ls -l`: `-rwxr-xr-x` shows execute bits

---

## Challenge 6: Permission Tweaking Practice

Practice various permission modification scenarios using chmod.

### Solution:
- used chmod a lot of times to change permissions
- 
- 

Use this blob for pasting commands you've run:
```sh
$ /challenge/run
$ chmod o-r /challenge/pwn
$ chmod g-r /challenge/pwn
$ chmod 
```

### Flag: 

```
pwn.college{8SK_CWzVvgpvGpniAPwEsDEZVpv.QXwEjN0wiN1EzNzEzW}
```

### Notes:
- `chmod u+r` adds read for user
- `chmod g-w` removes write for group
- `chmod o=r` sets others to read-only
- `chmod a+x` adds execute for all (a = all)
- Can combine: `chmod u+rw,g+r,o-rwx file`

---

## Challenge 7: Permissions Setting Practice

Practice setting absolute permissions rather than modifying existing ones.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- set permissions in chmod using `=` 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ 
$ 
```

### Flag: 

```
pwn.college{gKVEaYI4CQVH0wsKmtuY02Spcwe.QXzETO0wiN1EzNzEzW}
```

### Notes:
- `chmod u=rwx` sets exact permissions for user
- `chmod g=rx` sets exact permissions for group
- `chmod o=` removes all permissions for others
- `=` replaces permissions instead of adding/removing
- Can combine: `chmod u=rwx,g=rx,o=r file`

---

## Challenge 8: The SUID Bit

Learn about the SUID (Set User ID) special permission bit and its security implications.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- added suid to /challenge/getroot
- catted /flag through root shell from /challenge/getroot
- 

Use this blob for pasting commands you've run:
```sh
$ chmod u+s /challenge/getroot
$ /challenge/getroot
$ cat /flag
```

### Flag: 

```
pwn.college{EABv3XV3S-cRUy5sjdhOxc19Vyl.QXzEjN0wiN1EzNzEzW}
```

### Notes:
- SUID allows file to run with owner's privileges
- Shown as `s` in user execute position: `-rwsr-xr-x`
- `chmod u+s file` or `chmod 4755 file` sets SUID
- Security risk if misused (privilege escalation)
- Common on system utilities like `su`, `sudo`, `passwd`
- Capital `S` means SUID set but not executable

---

## References:

- [PWN College - Linux Luminarium Permissions](https://pwn.college/linux-luminarium/permissions/)
- [chmod Manual](https://man7.org/linux/man-pages/man1/chmod.1.html)
- [chown Manual](https://man7.org/linux/man-pages/man1/chown.1.html)
- [chgrp Manual](https://man7.org/linux/man-pages/man1/chgrp.1.html)
- [Linux File Permissions Guide](https://www.redhat.com/sysadmin/linux-file-permissions-explained)
- [SUID, SGID, and Sticky Bit](https://www.redhat.com/en/blog/suid-sgid-sticky-bit)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- Every file has an owner (user) and group
- Three permission types: read (r=4), write (w=2), execute (x=1)
- Three permission sets: user/owner, group, others
- `ls -l` displays permissions: `-rwxr-xr-x`
- First character: file type (-, d, l, etc.)
- Next 9 characters: permissions (3 each for u, g, o)
- `chmod` changes permissions (symbolic or octal)
- `chown` changes file owner
- `chgrp` changes file group
- SUID bit allows running with owner's privileges
- Octal notation: 755 = rwxr-xr-x, 644 = rw-r--r--

### Common Mistakes:
- Forgetting sudo when changing ownership
- Confusing symbolic and octal chmod notation
- Not understanding execute permission on directories
- Setting overly permissive permissions (777)
- Forgetting that SUID only works on executable files
- Mixing up user, group, and others permissions
- Not checking current permissions before modifying

### Alternative Methods:
- Symbolic vs octal chmod: `chmod u+x` vs `chmod 755`
- `chown user:group` vs separate `chown` and `chgrp`
- Setting SUID: `chmod u+s` vs `chmod 4755`
- Recursive permissions: `chmod -R` for directories
- Using `stat` for detailed permission info

### Octal Permission Reference:
```
0 = --- (no permissions)
1 = --x (execute only)
2 = -w- (write only)
3 = -wx (write and execute)
4 = r-- (read only)
5 = r-x (read and execute)
6 = rw- (read and write)
7 = rwx (all permissions)
```

### Security Considerations:
- Never use 777 permissions unless absolutely necessary
- SUID binaries are potential security vulnerabilities
- Limit file access using principle of least privilege
- Check for unexpected SUID files: `find / -perm -4000`
- World-writable files can be dangerous
- Directories need execute permission to access contents
