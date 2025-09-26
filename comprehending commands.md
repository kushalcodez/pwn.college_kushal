
# CAT NOT THE PET THE COMMAND

One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
```

## Solution:
- used cat flag

Use this blob for pasting commands you've run
```sh
$ cat flag
```

## Flag: 

```
pwn.college{4ODX4ExuR3DI2QHIiV2t2TZnsIq.QXxcTN0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- cat is used to concatenate multiple files if given multiple arguments
- cat is used to read out files

# CATTING ABSOLUTE PATHS

specify cat's arguments as absolute paths:

```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
```
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

## Solution:
- used absolute path for reading out file

Use this blob for pasting commands you've run
```sh
$ cat /flag
```

## Flag: 

```
pwn.college{kgbvqrGtwiv9g-fk-fqYhcctQZk.QX5ETO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- cat can be used on absolute paths aswell


# more catting for you 
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/include/editline/flag. Go cat it out **without** cding into 
that directory!
## Solution:
- used absolute path for reading out file which was in some other directory

Use this blob for pasting commands you've run
```sh
$ cat /usr/include/editline/flag
```

## Flag: 

```
pwn.college{Aay-xx7JNXDnwNaVLxbB07KPCB5.QXwITO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- more usage of cat for getting used to

# GREPPING FOR A NEEDLE IN A HAYSTACK
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:
```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.
```

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text `pwn.college.`

## Solution:
- used grep command to search for the flag since it starts with pwn.college
```sh
$ grep pwn.college /challenge/data.txt
```

## Flag: 

```
pwn.college{8QMBnlIYnGYFFwyjIs3V-UyEL6w.QX3EDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- when to find something specific in a very big set of data, cat cannot be used since it reads out everything therefore we use grep which searches for what specific we want and reads it out



# DIFFERENCE
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:
```
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

## Solution:
- used diff tag to find the difference between the two files
```sh
$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
```

## Flag: 

```
pwn.college{w29NaHFoZlaaFF_60A9BvOQ98RA.01MwMDOxwiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- when to find difference between two large files having almost the same data


# LISTING
So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:
```
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```
## Solution:
- used grep command to search for the flag since it starts with pwn.college
```sh
$ ls /challenge/
$ /challenge/13218-renamed-run-3277
```

## Flag: 

```
pwn.college{c0Ulj8uqJqfF0FWaWU8D6lP2fhP.QX4IDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- ls is used to list out all the files in a directory

# TOUCHING FILES
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```

## Solution:
- used touch command to create two files
```sh
$ touch /tmp/pwn
$ touch /tmp/college
```

## Flag: 

```
pwn.college{c5Yqaax7uflaRtANSSPfXJm3JZS.QXwMDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- Touch is used to create new empty files using the terminal

# REMOVING FILES
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:
```
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```
## Solution:
- used rm command to delete the file

Use this blob for pasting commands you've run
```sh
$ ls
$ rm delete_me
$ /challenge/check
```

## Flag: 

```
pwn.college{k6o1EVdXydALX_k-EnkH4niT9ab.QX2kDM1wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:

- rm command is used to delete files and is the opposite of the touch command
- pwn.college{sV9HGkVnJlIcfSLV-L_t1Y3h_ci.0VOxEzNxwiN1EzNzEzW}


# MOVING FILES
You can also move files around with the mv command. The usage is simple:
```
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
```
## Solution:
- used mv command to move /flag to /tmp/hack-the-world
- ran /challenge/check

Use this blob for pasting commands you've run
```sh
$ mv /flag /tmp/hack-the-world
$ /challenge/check
```

## Flag: 

```
pwn.college{sV9HGkVnJlIcfSLV-L_t1Y3h_ci.0VOxEzNxwiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:
- mv command is used to move files from one directory to another


# HIDDEN FILES
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:
```
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```
## Solution:
- used mv command to move /flag to /tmp/hack-the-world
- ran /challenge/check

Use this blob for pasting commands you've run
```sh
$ ls / -a
$ cat /.flag-60291560826816
```

## Flag: 

```
pwn.college{cZ96oYogB1kVNZg_SCWhGYjEKQC.QXwUDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:
- we use the -a argument to access hidden files

# AN EPIC FILESYSTEM QUEST
With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:
```
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
```
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

1.Your first clue is in /. Head on over there.
2.Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
3.cat that file to read the clue!
4.Depending on what the clue says, head on over to the next directory (or don't!).
5.Follow the clues to the flag!
## Solution:
- used ls for accessing files inside a directory without cd'ing into it
- used cat for reading
- used ls -a for accessing hidden files
Use this blob for pasting commands you've run
```sh
$ ls /
$ cat /TIP
$ cd  /usr/share/icons/ubuntu-mono-dark/places/22
$ cat /usr/local/lib/python3.8/dist-packages/nbformat/v4/SNIPPET
ls /opt/linux/linux-5.4/drivers/media/platform/meson
cat /opt/linux/linux-5.4/drivers/media/platform/meson/MESSAGE-TRAPPED
ls /usr/share/racket/pkgs/net-cookies-doc/net/cookies
cat /usr/share/racket/pkgs/net-cookies-doc/net/cookies/INSIGHT
ls /usr/share/racket/pkgs/htdp-lib/2htdp/planetcute/compiled -a
cat /usr/share/racket/pkgs/htdp-lib/2htdp/planetcute/compiled/.README
ls /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/stdlib/3/collections
cat /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/stdlib/3/collections/MEMO-TRAPPED
ls /usr/lib/python3/dist-packages/twisted/conch/test/__pycache__
cat /usr/lib/python3/dist-packages/twisted/conch/test/__pycache__/GIST
ls /usr/share/javascript/three/examples/js/controls -a
cat /usr/share/javascript/three/examples/js/controls/.CUE
```

## Flag: 

```
pwn.college{UDAMwZq-88oI5BzZGtqTEn_PC0L.QX5IDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:
- used cd cat ls and ls -a to access and read different files and directories

# MAKING DIRECTORIES
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```
## Solution:
- used mkdir to make a directory and then used touch to make the file

Use this blob for pasting commands you've run
```sh
$ mkdir /tmp/pwn
$ touch /tmp/pwn/college
$ /challenge/run
```

## Flag: 

```
pwn.college{AeA5JII0GlKY4fChyemRpe7duaJ.QXxMDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:
- we use the mkdir command to create directories


# FINDING FILES
So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.). For example:
```
hacker@dojo:~$ mkdir my_directory
hacker@dojo:~$ mkdir my_directory/my_subdirectory
hacker@dojo:~$ touch my_directory/my_file
hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find
.
./my_directory
./my_directory/my_subdirectory
./my_directory/my_subdirectory/my_subfile
./my_directory/my_file
hacker@dojo:~$
```
And when specifying the search location:
```
hacker@dojo:~$ find my_directory/my_subdirectory
my_directory/my_subdirectory
my_directory/my_subdirectory/my_subfile
hacker@dojo:~$
```
And, of course, we can specify the criteria! For example, here, we filter by name:
```
hacker@dojo:~$ find -name my_subfile
./my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find -name my_subdirectory
./my_directory/my_subdirectory
hacker@dojo:~$
```
You can search the whole filesystem if you want!
```
hacker@dojo:~$ find / -name hacker
/home/hacker
hacker@dojo:~$
```
## Solution:
- used find command in the home directory with name specifier as flag
- hit and trial method to find the flag since there are multiple files in different directories with the name flag

Use this blob for pasting commands you've run
```sh
$ find / -name flag
$ cat /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Neo-Euler/Arrows/Regular/flag
```

## Flag: 

```
pwn.college{gwtmcq99qFlV1fCar9Prz6V8Q2e.QXyMDO0wiN1EzNzEzW}
```


### References:

- (https://pwn.college)
- 
### Notes:
- we use find command to find some file in a directory/filesystem
- -name is used to specify the name of the file to be found


# LINKING FILES
If you use Linux (or computers) for any reasonable length of time to do any real work, you will eventually run into some variant of the following situation: you want two programs to access the same data, but the programs expect that data to be in two different locations. Luckily, Linux provides a solution to this quandary: links.

Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.
In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediately yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file. In most cases, both situations result in accessing the original data, but the mechanisms are different.

Hard links sound simpler to most people (case in point, I explained it in one sentence above, versus two for soft links), but they have various downsides and implementation gotchas that make soft/symbolic links, by far, the more popular alternative.

In this challenge, we will learn about symbolic links (also known as symlinks). Symbolic links are created with the ln command with the -s argument, like so:
```
hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
```
You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:
```
hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
```
## Solution:
- removed the already existing symbolic link by removing the file itself then made another symbolic link with flag and then executed.
Use this blob for pasting commands you've run
```sh
$ rm ./not-the-flag
$ ln -s /flag ./not-the-flag
$ /challenge/catflag
```

## Flag: 

```
pwn.college{U5n4eo8EzeTnJ2fJCV1VdY8NfGc.QX5ETN1wiN1EzNzEzW}
```

# NOTES :
symbolic links are basically 2 files which lead to the same output.
