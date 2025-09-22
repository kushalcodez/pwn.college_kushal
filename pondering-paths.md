# Challenge 1 The Root

In this challenge, you will learn to navigate to the root directory. The root directory is the top-level directory in the Linux filesystem, represented by a single forward slash `/`.

## Solution:

The user needs to navigate to the root directory and run the challenge.

#### Commands run: 

```sh
$ /pwn
```

## Flag: 

```
pwn.college{EYDj6-7spJS-9_KkIgrBHWedPqr.QX4cTO0wiN1EzNzEzW}
```

### Notes:

- The root directory is accessed using `/`
- Absolute paths start from the root directory

# Challenge 2 Program and Absolute Paths

In this challenge, you will learn to run programs using their absolute paths. An absolute path specifies the complete path from the root directory to the target file.

## Solution:

The user needs to run the challenge program using its absolute path.

#### Commands run: 

```sh
$ /challenge/run
```

## Flag: 

```
pwn.college{MMndnP5353_kzqmHxiNH-2lAVHj.QX1QTN0wiN1EzNzEzW}
```

### Notes:

- Absolute paths always start with `/`
- You can run programs by specifying their full path

# Challenge 3 Position Me

In this challenge, you will learn to change directories using the `cd` command and then run programs from different locations.

## Solution:

The user needs to change directory to `/etc` and then run the challenge.

#### Commands run: 

```sh
$ cd /etc
$ /challenge/run
```

## Flag: 

```
pwn.college{sAlr3NeoWZMz6dXK48UgjpllC3N.QX2QTN0wiN1EzNzEzW}
```

### Notes:

- `cd` command is used to change directories
- You can run programs from any directory using absolute paths

# Challenge 4 Position Elsewhere

In this challenge, you will navigate to a more complex directory path and run the challenge from there.

## Solution:

The user needs to change to a specific process directory and run the challenge.

#### Commands run: 

```sh
$ cd /proc/136/fd
$ /challenge/run
```

## Flag: 

```
pwn.college{42z4g8KPOnvPQ5M-bKlP3W8ZMIE.QX3QTN0wiN1EzNzEzW}
```

### Notes:

- `/proc` directory contains process information
- You can navigate to deeply nested directories

# Challenge 5 Position Yet Elsewhere

In this challenge, you will practice navigating to the root directory and running the challenge.

## Solution:

The user needs to change to the root directory and run the challenge.

#### Commands run: 

```sh
$ cd /
$ /challenge/run
```

## Flag: 

```
pwn.college{sHnfB9OM-OEqgGts8gvTIbJHszt.QX4QTN0wiN1EzNzEzW}
```

### Notes:

- The root directory `/` is the top-level directory
- All absolute paths start from the root directory

# Challenge 6 Implicit Relative Paths from Root

In this challenge, you will learn about relative paths and how they work from different directories.

## Solution:

The user needs to navigate to root and use a relative path to run the challenge.

#### Commands run: 

```sh
$ cd /
$ challenge/run
```

## Flag: 

```
pwn.college{MFzoYnOcfh5VfuLAPpCh2q33z2k.QX5QTN0wiN1EzNzEzW}
```

### Notes:

- Relative paths are relative to your current working directory

# Challenge 7 Explicit Relative Paths from Root

In this challenge, you will learn to use explicit relative paths and change directories in a single operation.

## Solution:

The user needs to change to the challenge directory and run the program relatively.

#### Commands run: 

```sh
$ cd /challenge
$ ./run
```

## Flag: 

```
pwn.college{4qzlbsGstITrLD-_ycawU-RqEZS.QXwUTN0wiN1EzNzEzW}
```

### Notes:

- You can change to a directory and then run programs within it
- `./run` executes the program in the current directory

# Challenge 8 IMPLICIT RELATIVE PATH
In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:
```
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```
This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:
```
bash: run: command not found
```

We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. 
## SOLUTION
The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!
###COMMANDS RUN
```
cd /challenge 
./run
```
## FLAG
```
pwn.college{wZ6TSAZJwcOj_2VYw3-raARCz4_.QXxUTN0wiN1EzNzEzW}
```
####NOTES
Linux doesnt run some files whose names sometimes are same as that of some system programs, therefore to run them we have to implicitly 'tell' linux to run.

# Challenge 9 HOME SWEET HOME

In this challenge, you will use implicit relative paths with arguments to run the challenge program.

## Solution:

The user needs to run the challenge program with a specific argument using a relative path.

#### Commands run: 

```sh
$ /challenge/run ~/a
```

## Flag: 

```
pwn.college{Yssg0BRqCqR1BClGpoSANSsDegb.QXzMDO0wiN1EzNzEzW}
```

### Notes:

- `~` represents the home directory
- Arguments can be paths to files or directories
- You can pass arguments to programs when running them
