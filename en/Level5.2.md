# Line by line analysis



~~~~~~~~
#!/usr/bin/env python
import re
f=open('MG1655-K12.fasta','r')
lines=f.readlines()
hre=re.compile('>(\S+)')
lre=re.compile('^(\S+)$')
gene={}
i=0
for line in lines:
        i=i+1
        if (i>66000):
                print i
        outh = hre.search(line)
        if outh:
                id=outh.group(1)
        else:
                outl=lre.search(line)
                if(id in gene.keys()):
                        gene[id] += outl.group(1)
                else:
                        gene[id] =outl.group(1)
~~~~~~~~

## General guidelines

For understanding the code, you need to keep a notebook, where you will write down the state of the program. I will explain what that means.
In the notebook, create three columns - line number, variables and libraries. In the line number, the computer is at 2.

## line 1

A computer runs program linearly, unless told otherwise. That means it starts the execution from line 1 and ends at the last line.
In case of above script, the computer comes in, reads the first line and runs the python interpretator to execute remaining lines.

## line 2

Python interpretator reads the second line and learns to import a library `re`. So far so good. On your notebook, 
add re


The variables column is empty. The libraries column has `re`.


## line 3

Now the computer goes to line 3 and sees `f=open('MG1655-K12.fasta','r')`
It creates a variable `f` and links to the file `MG1655-K12.fasta` in the physical directory (disk). Now you have `f` in the variables column.



## line 4

The computer sees `lines=f.readlines()`. What is `f`? It is the E coli file. What is `lines`? It is a new variable. So, you have `f` and `lines` in the variables column.
Also, at this line, the computer is asked to read the file `f` (`readlines` function) and store in `lines`. That means `lines` is a variable of type array. I also forgot to mention that `f` is a variable of type file.



## lines 5,6

The computer creates two new variables `hre` and `lre` using the compile function from `re` library. Those two variables are of regular 
expression type.  How many variables do we have in the variables column? - `f` (file), `lines` (array of string), `hre` (reg exp), 
`lre` (reg exp).


#lines 7, 8

Two new variables - `gene` (and empty array) and `i` (integer with value 0).


#line 9
Now the fun begins. Remember - the computer runs a program from the first to the last line, unless told otherwise.
`for` command is one way to tell the computer otherwise. The `for` command asks the computer to keep looping through the next set of lines, until a condition is satisfied. That condition is `line in lines`.
That means the computer will keep looping through the next few lines for 66284 times. Why? Because the array `lines` has that many entries.
Question for everyone - what do you have in the variables column now?
anyone with me?

So our variables are now:
`f` (file), `lines` (array of string), `hre` (reg exp), `lre` (reg exp), and gene` (and empty array) and `i` (integer with value 0).
Great !
We do have an extra variable after line 9, and it is `line`.
The rest are as 

# line 10
The value of `i` is now `i+1`. That means `i` has become 1 now.



#line 11,12
The computer asks `if (i>66000):`
Only if the answer is yes, the computer goes to the next line. Otherwise, jumps straight to line 13.


# line 13

`outh = hre.search(line)`
The computer runs the function - `hre.search(line)`. This function returns 1, if variable `line` matches the regular expression `hre`.

because we declare it as 
```
hre =re.compile('>(\S+)')
```
in the start so it will be looking for the fasta header.



That is correct about `hre`, but what is `line` in line 13 now? (and why)?

Is it the next line down from the > line?
in the fasta file, i mean. the following line?


No, it is the first line in the FASTA file. Let us go back to see where the `line` variable comes from. The variable is defined in 9th line of the code, which starts the `for` loop.

What if the file is multi-fasta?

The variable is defined as the first element of the `lines` array, which means the first line of the FASTA file. That is because the computer read the entire FASTA file and stored in multiple entries of the `lines` variable.

would that change if there is a new fasta header on line 12?

the command `f.readlines` reads a file with text and saves in an array. Whatever is in the first line of the file will be in `lines[0]` of the array. Whatever is in the second line, will be `lines[1]` and so on.
If there is a new fasta header on line 12, that will be `lines[12]` in the array.
The entire file (in the disk) is being read into an array, which is a variable within the program.


Maybe expanding on what X said, and oi may not be understanding, but it seems like the program is having a difficult time treating the entire e. coli genome as a single array, and adding line after line

So if we reset the array, the program would be able to process it without having start at the beginning of the fasta file each time

The program is going through the entire file in the disk only once. That is minimum of what one can do.
The entire `for` loop from l line 9 to the end runs once for every line in the FASTA file.
When it runs the first time, the variable `line` has the first line of the file. So, the rest of the code checks for regular expression, finds a match with `hre` and determines that it is a FASTA header. The program acts accodingly.
What does act accordingly mean? The program works through these two lines -
(edited)
```
if outh:
                id=outh.group(1)
```
That means, if `outh` is 1, the program creates another new variable named `id` and stores the value defined by `outh.group(1)`.
What is `outh.group(1)`? To find that out, we need to go back to the definition of the regular expression `hre`, because `outh` is the outcome of that regular expression search. What is `hre`? It is `hre =re.compile('>(\S+)')`.
You see `\S+` in first bracket. That means any text in `line` that matches as `\S+` will be returned by the code as `outh.group(1)`.
What does that mean? To trace back, we need to look at the `line` variable. That variable has the first line of the FASTA file, which happens to have the FASTA header. The regular expression searches through the FASTA header and finds out the text right after `>`.
That is returned as `id=outh.group(1)`.



#!/usr/bin/env python
import re
f=open('MG1655-K12.fasta','r')
lines=f.readlines()
hre=re.compile('>(\S+)')
lre=re.compile('^(\S+)$')
gene={}
i=0
for line in lines:
i=i+1
if (i>66000):
print i
outh = hre.search(line)
if outh:
id=outh.group(1)
print id
with the accompanying indents - they did not copy over unfortunately


you may add the line `exit(0)` after the print command. That way it will exit right after executing the command and you will not see the rest of the output from the other lines.
`exit(0)`
the slowdown comes from this line `gene[id] += outl.group(1)`
What is the line doing? The command `+=` means it adds a string at the end of the existing string.
Think about doing the same on your notepad. What will happen?

