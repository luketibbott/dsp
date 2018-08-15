# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > `pwd` - print working directory
> > `mkdir [name]` - creates directory titled "name"
> > `rmdir` - delete empty directory
> > `touch [filename]` - create file
> > `rm [filename]` - delete file
> > `mv [filename] [newfilename]` - rename file
> > `ls -a` - list all files in current directory, including hidden files
> > `cp [source] [destination]` - copies source file to destination path
> > `cd [destination] - changes current directory to destination path
> > `grep 'pattern' [file]` - search given file for text that matches pattern

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > `ls` - list contents of directory in alphabetical order
> > `ls -a` - list hidden and non-hidden contents of directory in alphabetical order
> > `ls -l` - list contents of directory in long-listing format
> > `ls -lh` - list contents of directory in long-listing format, human-readable form
> > `ls -lah` - list all contents of directory in human-readable long-listing format
> > `ls - t` - list contents of directory sorted chronologically (by modification time)
> > `ls -Glp` - list contents of directory in long-listing format, with '/' after directory names, without directory group names printed

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > `ls -c` Display files by file timestamp
> > `ls -m` Display names as a comma-separated list.
> > `ls -q` Display all nonprinting characters as '?'.
> > `ls -R` Display subdirectories as well.
> > `ls -1` Display each entry on a line.

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > xargs essentially takes the standard input of a command (eg `ls` or `pwd`) and converts the input into arguments of a different command.

> > An example is something like `find *.txt` | xargs rm` . This example executes `rm` on all .txt files returned by `find`. 

 

