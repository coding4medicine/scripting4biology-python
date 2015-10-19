# Linux basics

Everything in unix is case sensitive. You can have two files - ME and me in the same folder. Windows does not allow that.


##  Commands to know about processor, memory, disk and processor

The following command gives you information about the processor and operating system.

~~~~~~~~
uname -a
~~~~~~~~

Disk -

~~~~~~~~
df -h
~~~~~~~~

RAM -

~~~~~~~~
free -g
~~~~~~~~

Network -

~~~~~~~~
netstat -a
~~~~~~~~


## Creating files and folders

Here are a set of linux commands you will find handy. Replace 'filename' with the name of the actual file.

| Task        |       Command         |
|-------------|-----------------------|
| Create file |  touch filename       |
| Edit file   |  nano filename        |
| Rename file | mv old-name new-name  |
| Delete file |  rm filename          |
| Create another copy |  cp old-name new-name |
| Create folder| mkdir foldername     |
| Move file inside folder |  mv filename foldername | 
| Move folder1 inside folder2 |  mv foldername1 foldername2 |
| Delete folder |  rmdir foldername    |

Please note that the command 'mv' has different purposes, depending on the context.


## Moving your current location between folders


| Task        |       Command         |
|-------------|-----------------------|
| Go inside directory |  cd foldername|
| Go back to your home dir| cd |
| Check in which directory currently| pwd | 
| List files in the folder|  ls |



## Command to see the files

| Task        |       Command         |
|-------------|-----------------------|
| Type content of file on screen | cat filename | 
| Type content of file - page by page|  more filename | 
| Count number of lines in a file |   wc filename|
| Print lines of file with the word 'dog' |  grep 'dog' filename|
| Print lines of file without the word 'dog'| grep -v 'dog' filename|



## Quick processing of files


| Task        |       Command         |
|-------------|-----------------------|
|Sorting a file| sort filename|
|Extracting second column of a file| cut -f 2 filename|
|Joining two files| paste file1 file2|
|Printing unique lines only | uniq filename|

Some variations -

'sort' sorts alphabetically, whereas 'sort -n' sorts numerically.

'uniq' gives unique lines in a file, whereas 'uniq -c' also adds counts.


We will learn more about the above commands, but let us first discuss a few shortcuts and symbols.

## Sending output to file instead of screen

In UNIX, you can send the output of a command into a directory.

For example, The output of following command goes on the screen.

~~~~~~~~
grep -P 'cat' file
~~~~~~~~


The output of following command goes in a file name file2.
~~~~~~~~
grep -P 'cat' file > file2
~~~~~~~~


## Combining multiple commands


In UNIX, you can combine multiple commands by using '|'.

For example, let's cut the first column of a file, sort the result and then count how many times each word appears. The command is -

~~~~~~~~
cut -f 1 file | sort | uniq -c
~~~~~~~~

