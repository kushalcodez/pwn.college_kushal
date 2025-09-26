
# LEARNING FROM DOCUMENTATION

The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, on the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

## Solution:
- gave the argument --giveflag similar to how we did ls -a

Use this blob for pasting commands you've run
```sh
$ /challenge/challenge --giveflag
```

## Flag: 

```
pwn.college{Y-T_PLxdSZE8H0fkIyQmgcYJOva.QX0ITO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

to access something specific from a document we can use arguments



# LEARNING COMPLEX USAGE

While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

## Solution:
- used /challenge/challenge --printfile argument to print the flag

Use this blob for pasting commands you've run
```sh
$ /challenge/challenge --printfile /challenge/challenge
/challenge/challenge --printfile /flag
```

## Flag: 

```
pwn.college{MRMQHbhgFgzUUoDy7kRs_mj8Ybc.QX1ITO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

documentation can be used to learn arguments and their implementation


# MANUAL READING

This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):
```
hacker@dojo:~$ man yes
```
This will display the manual page for yes, which will look something like this:
```
YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
```
## Solution:

Describe your thought process and solve, write as much as possible with steps:

- opened challenge manual to get the argument required for flag 

Use this blob for pasting commands you've run
```sh
$ man challenge
$ /challenge/challenge --obfgyq 070
```

## Flag: 

```
 pwn.college{YoUAbfgLy0qN_fxKiaxaDazult7.QX0EDO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

manual reading


# MANUAL SEARCHING

You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

## Solution:

- opened the manual for challenge and searched for the arguement with flag

Use this blob for pasting commands you've run
```sh
$ man challenge
/flag 
n
/challenge/challenge --anav
```

## Flag: 

```
pwn.college{Ul2ktMUI5x--LLvKXdPy2u29z7X.QX1EDO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

searching through a manual when there are a lot of arguements


# SEARCHING FOR MANUALS
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!

## Solution:

checked the manual manual for knowing arguments for manuals, then used the -k argument with flag keyword to find the manual with the flag

Use this blob for pasting commands you've run
```sh
$ man man
man -k flag
man oymfhzprsw
/challenge/challenge --oymfhz 817
```

## Flag: 

```
pwn.college{o8T1yAmfGhOU_zNJ7KZp1r36sMV.QX2EDO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

we can search for different manuals using -k argument


# GETTING HELP
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).
## Solution:
- used /challenge/challenge --help and followed instructions based on the help given

Use this blob for pasting commands you've run
```sh
$ /challenge/challenge --help
/challenge/challenge -p
/challenge/challenge -g 728
```

## Flag: 

```
pwn.college{w7_X2X8sYU__myHFlNuGslr2-JO.QX3IDO0wiN1EzNzEzW}

```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

--help is used if we want any help regarding a program and can be used with any program



# HELP FOR BUILTINS
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:
```
hacker@dojo:~$ help
```
You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!
```
hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
...
```
## Solution:
- used help command with challenge

```sh
$ help challenge
challenge --secret 8NIi0l_0
```

## Flag: 

```
pwn.college{8NIi0l_0EZ22Aya4svF2-kESgY_.QX0ETO0wiN1EzNzEzW}
```


### References:

- [link 1](https://pwn.college)
- 
### Notes:

we can use the help command for builtins aswell

