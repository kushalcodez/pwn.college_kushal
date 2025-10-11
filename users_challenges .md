# PWN College - Linux Luminarium: Untangling Users Challenges

## Challenge 1: Becoming root with su

Use the `su` (substitute user) command to become root. In this challenge, the root password is "hack-the-planet". Use su to become root and read the flag.

### Solution:

- used su to become root
- cat /flag to get flag
- 

Use this blob for pasting commands you've run:
```sh
$ su
hack-the-planet #password
$ cat /flag
```

### Flag: 

```
pwn.college{k5dvrQ_jREq_HFlLSqKoWZKxTYk.QX1UDN1wiN1EzNzEzW}
```

### Notes:
- `su` stands for "substitute user" (not switch user)
- `su` without arguments switches to root user
- `su` is a SUID binary (runs with root privileges)
- When run, `su` checks the password before allowing privilege elevation
- The password for this challenge is: `hack-the-planet`
- After successfully authenticating, you get a root shell
- Modern systems rarely have root passwords; sudo is preferred
- Use `exit` or Ctrl+D to return to original user

---

## Challenge 2: Other users with su

Practice switching to users other than root using the `su` command.

### Solution:

- used su to switch user to zardus and then used /challenge/run

Use this blob for pasting commands you've run:
```sh
$ su zardus
dont-hack-me #password
$ /challenge/run
```

### Flag: 

```
pwn.college{E7JmqXdru3Cp3tnHhF_OfH6uZDI.QX2UDN1wiN1EzNzEzW}
```

### Notes:
- `su username` switches to any user (not just root)
- Each user has their own home directory and permissions
- Need to know the target user's password
- The new shell inherits the target user's environment
- Check current user with `whoami` command

---

## Challenge 3: Cracking passwords

Learn about password storage and cracking techniques in Linux systems.

### Solution:

- used john the ripper on /challenge/shadow-leak
- switched to zardus
- ran /challenge/run

Use this blob for pasting commands you've run:
```sh
$ john /challenge/shadow-leak
$ su zardus
aardvark
$ /challenge/run
```

### Flag: 

```
pwn.college{08bhrbaR-o2RdTz835-t1W_PQgF.QX3UDN1wiN1EzNzEzW}
```

### Notes:
- Passwords are stored as hashes in `/etc/shadow`
- `/etc/passwd` used to store passwords (hence the name)
- Only root can read `/etc/shadow`
- Password hashes use algorithms like SHA-512
- Tools like John the Ripper can crack weak passwords
- Strong passwords are essential for security

---

## Challenge 4: Using sudo

Learn to use `sudo` to execute commands with root privileges without switching users.

### Solution:
- used sudo for getting flag
- 
- 

Use this blob for pasting commands you've run:
```sh
$ sudo cat /flag
$ 
```

### Flag: 

```
pwn.college{0djGJZFXaRebgM128seIz1V3iIr.QX4UDN1wiN1EzNzEzW}
```

### Notes:
- `sudo command` runs command as root
- More modern and secure than `su`
- Uses your own password, not root's password
- Configured in `/etc/sudoers` file
- Only authorized users can use sudo
- Logs all sudo usage for auditing
- Example: `sudo cat /etc/shadow`

### Notes:
- `sudo -u username command` runs command as specified user
- `sudo -i` gets an interactive root shell
- `sudo -s` starts a shell as root
- `sudo su` combines both tools (sudo to run su)
- More flexible than plain `su`
- Respects sudoers configuration

---

## References:

- [PWN College - Linux Luminarium Users](https://pwn.college/linux-luminarium/users/)
- [su Manual](https://man7.org/linux/man-pages/man1/su.1.html)
- [sudo Manual](https://man7.org/linux/man-pages/man8/sudo.8.html)
- [Understanding /etc/passwd](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)
- [Understanding /etc/shadow](https://www.cyberciti.biz/faq/understanding-etcshadow-file/)

## Notes:

Include things you learnt, alternate methods or mistakes you made while solving:

### Key Concepts Learned:
- Linux is a multi-user system with user separation
- `/etc/passwd` contains user account information
- `/etc/shadow` contains password hashes (root-only)
- `root` user (UID 0) has full system privileges
- `su` switches user accounts (older method)
- `sudo` executes commands with elevated privileges (modern method)
- SUID bit allows programs to run with owner's privileges
- Password cracking targets weak passwords
- User privileges are fundamental to Linux security

### Common Mistakes:
- Forgetting password when using `su`
- Not having sudo privileges configured
- Confusing `su` and `sudo` usage
- Trying to access `/etc/shadow` without root privileges
- Not using `exit` to return to original user after `su`
- Running `sudo su` when `sudo -i` would suffice

### Alternative Methods:
- `su -` vs `su` (with vs without login environment)
- `sudo -i` vs `sudo -s` vs `sudo su`
- `sudo -u user command` vs `su user -c command`
- Using `whoami` vs `id` to check current user
- `sudo !!` to re-run previous command with sudo

### Security Considerations:
- Root access should be carefully controlled
- Use sudo instead of logging in as root
- Strong passwords prevent cracking attacks
- Audit sudo logs to detect misuse
- Principle of least privilege: only grant necessary permissions
- SUID binaries can be security vulnerabilities if misconfigured
