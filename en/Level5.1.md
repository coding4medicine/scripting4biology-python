# Describing How to Code (Based on Code for Reading a FASTA File)


Today we will do something different. I will explain how a program for a given problem is written from scratch, and all the trial-and-error that goes behind it. The example we choose is the one I sent out in the previous hand-out, namely the code for reading a FASTA file. I will explain the python version, but  the thought process behind the PERL version follows similar logic.

The task at hand is to read a FASTA file. You know that FASTA format has the ID and sequence for a number of genes. The ID line starts with '>' and may have additional text following the identifier. The sequence can be split into multiple lines. There can be empty sentences in between two genes.



## Step 1. Reading each line

First, we will write a code that reads the lines from a given file. As you write more and more codes, you will find that you are dealing with this question almost always. Therefore, it is prudent to have a couple of templates for reading files ready somewhere in your directory. We will evaluate those templates and explain the pros and cons of each.

Template 1.

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
lines=f.readlines()
~~~~~~~~


Template 2.

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
line1=f.readline()
line2=f.readline()
~~~~~~~~

In both templates, 'f' is the identifier for the file 'genes.fasta'. That means wherever the symbol 'f' occurs  in the rest of the code, the computer will know that it has to process the 'genes.fasta' file. 

The second thing you notice is that the 'open' statement contains the option 'r'. That means the file is opened for read only, which is appropriate for our task here. You may have to choose other options for different tasks.

Why does python use this method of creating a file identifier (f) instead of using the actual name of the file in the entire code? There are two advantages. First, the file name can be very long, and the programmer may not like to clutter the program with that long text. The second and more important reason for using file identifier is that the filename may not be known before one runs the program. For example, it is very common to specify the filename as a command line option.

Next, let us discuss the differences between template 1 and template 2. In template 1, the entire file 'genes.fasta' is read in an array named 'lines'. Each element of the array is a string that holds a line from the FASTA file. In template 2, the file needs to be read line-by-line. In the example given above, we read only two lines and store them in strings line1 and line2.

You can see that template 1 is really convenient for programming, because the entire file is read in an array within the code and that array can be processed using 'for', ', we can process the array within our code. However, there are some disadvantages of doing so, when it comes to bioinformatics. Some FASTA files can be very big. You certainly do not always want to load the entire human genome using a 'readlines' statement.

Here is how the programmers write code. They keep the above constraint at the back of the mind and then start with the simple option. If that fails, then they take a step back and modify their code with the more difficult option. Therefore, let us first go with Template 1 for our code.  Here is our code at the end of step 1.

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
lines=f.readlines()
~~~~~~~~

After completion of every step, it is prudent to test and make sure the code works. Let us do that after the above step and add a print statement. Since lines array reads the 'genes.fasta' files, a statement line 'print lines[3]' will print the third line. You can try it out.

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
lines=f.readlines()
print lines[3]
~~~~~~~~


Oops, there is a problem.

~~~~~~~~
Traceback (most recent call last):
  File "./c.py", line 2, in <module>
    f=open('genes.fasta','r')
IOError: [Errno 2] No such file or directory: 'genes.fasta'
~~~~~~~~

You realize that you either do not have a file named 'genes.fasta' or the file is not in the same directory as the python script.

Once you handle the above problem, you will notice two things - 
(i) The program is printing the fourth line instead of the third line. What is going on? By playing with different indices in the print statement, you find out that the array 'lines' stores the lines with indices 0,1,2,3,.....
(ii) The program is printing an extra newline after the third line. Why so? The program is printing lines[3] from the file including the newline, and if you remember, python print command adds an extra newline after each statement. Hence you have one extra empty line. The best option is to remove newline from the end of lines[3]. The command for that is lines[3]=lines[3].rstrip('\n'). This command removes the newline from the end of lines[3] and saves it as the new lines[3]. Run the following code and you see it working fine.

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
lines=f.readlines()
lines[3]=lines[3].rstrip('\n')
print lines[3]
~~~~~~~~

Why not remove the newline from all lines? You try this code -

~~~~~~~~
#!/usr/bin/env python
f=open('genes.fasta','r')
lines=f.readlines()
lines=lines.rstrip('\n')
print lines[3]
~~~~~~~~

and get the error -

~~~~~~~~
Traceback (most recent call last):
  File "./c.py", line 4, in <module>
    lines=lines.rstrip('\n')
AttributeError: 'list' object has no attribute 'rstrip'
~~~~~~~~

Oops, seems like trouble. What is going on? As it happens, the command rstrip('\n') can only work on strings, or each element of the lines array, but not on the entire array at the same time. Let us keep this at the back of the mind and revisit later, if needed.




## Step 2. Processing the ID

Let us now move on to processing the lines of the file, which are now stored in 'lines' array. We will first look for the FASTA ID. You know that the first line has a FASTA ID after '>'. So, let us see, whether we can write code to extract the ID. 

The method to do that is to create a regular expression. So, it is good time to review the unix 'grep' commands and python regular expression command, which came from 'grep'. The syntax for regular expression is as follows.

~~~~~~~~
#!/usr/bin/env python
import re
f=open('genes.fasta','r')
lines=f.readlines()
hre=re.compile('>(\S+)')
outh = hre.search(lines[0])
if outh:
    print outh.group(1)
~~~~~~~~

When you compare with previous program, you will notice that we added a few extra lines. 

i) The first extra line says 'import re'. That is to tell python that we are using the regular expression library.

ii) The second extra line is 'hre=re.compile('>(\S+)'). This line defines a regular expression named 'hre'. The regular expression looks for the presence of '>\S+' in a line, or the presence of '>' followed by some non-whitespace text. What are the brackets for? If you put bracket in a regular expression, that is useful for returning the exact block that matches the text. Therefore, the above command will return the text that comes after '>' symbol or it is the ID in the context of a FASTA format.

iii) The third extra line is 'outh = hre.search(lines[0])'.
This line searches for 'hre' in lines[0]. If the search finds a match, the variable 'outh' is 1. If not, it is 0.

iv) The fourth part should be clear from the above description. If there is a match with lines[0], the program goes inside the 'if' section and prints 'outh.group(1)', which is the matched part inside the bracket.

I encourage you to change the regular expression and try it on various lines to see what you get.



## Step 3. Processing the non-ID lines from FASTA file

You know that the FASTA file has other lines, which contain nucleotide or protein sequences. How do we extract data from them? The answer is regular expression again. We create another regular expression for the non-ID lines. Our code grows to -

~~~~~~~~
#!/usr/bin/env python
import re
f=open('genes.fasta','r')
lines=f.readlines()
hre=re.compile('>(\S+)')
lre=re.compile('^(\S+)$')
outl = lre.search(lines[1])
if outl:
    print outl.group(1)
~~~~~~~~

Here we are trying a second regular expression 'lre'. This regular expression looks for '^(\S+)$'. What that means is it is searching for a line that is entirely non-whitespace characters (\S+). The '^' at the beginning and '$' at the end make sure the search string matches the entire line, excluding the terminal newline.

To understand how it works, you need to try the code yourself. No matter of description can make this clear.



## Step 4. Data structure

Alright. Now that we know how to process each line of the file, the task is to process the entire file and store into something within the code. What is that 'something' going to be? We need to decide about a data structure. Data structure is the method to store data within your program. For individual data, you can hold in string, integer or decimal data structure. For collection of data, you need something like array or associative array. 

As you continue to write more and more programs, you will realize that the data structure question becomes very important in your work. In fact, it is one of the two major components of programming, the other one being algorithm. After you master a language, you will find the language to be of less importance in day to day work.

Getting back to data structure question, it is clear that you can use string format to hold each gene or protein sequence. For the collection of genes, you need to use something like an array. In fact, you will need two arrays – one to store the ID and the other to hold the sequence. So, the format  is  ID_array[0]='ID1' and seq_array[0]='ATGTGGGAGGAAGGTGGGTGAAA', and so on.

Is that the best data structure? You can answer only by thinking about what kind of questions you will have to answer in your program. In bioinformatics, often you will come across questions like 'what is the sequence of gene ID2?' To answer that, you will have to first go over the entire ID_array to find the coordinate of gene ID2 and then you go to seq_array to find its sequence. That entire process is time-consuming and you need a better data structure to answer the question very rapidly. 

An associative array becomes a better answer in this case. In case of associative array, you will need only one array, whose identifiers are FASTA Ids and values are sequences. It will look like  fasta_array['ID1']='ATGTGGGAGGAAGGTGGGTGAAA', and so on for the rest of the genes. 


In our program, we will use associative arrays. What does that mean for the actual code? Let us open a different file and try a simple example. 

~~~~~~~~
#!/usr/bin/env python
gene={}
gene['ID1']='AAAAA'
gene['ID2']='ATGGTG'
print gene
~~~~~~~~

You will see that the program prints {'ID2': 'ATGGTG', 'ID1': 'AAAAA'}. We have the syntax for an associative array. The next step is to combine it with the regular expression blocks from the other steps.



## Step 5. For loop and final code

The associative array 'gene' is the perfect data structure for our code, because it saves FASTA IDs and sequences as pairs. However, instead of telling the program that 'gene['ID1']='AAAA' and so on, we need to enter values into 'gene' based on processed FASTA file. That means you need a for loop to go over the elements of the array 'lines', process each line to find the ID or the sequence and keep adding information to the associative array 'gene'. The program turns into -

~~~~~~~~
#!/usr/bin/env python
#####################
# code to read FASTA file
#####################
import sys, re

f=open('genes.fasta','r')
lines=f.readlines()

hre=re.compile('>(\S+)')
lre=re.compile('^(\S+)$')

gene={}

for line in lines:
        outh = hre.search(line)
        if outh:
                id=outh.group(1)
        else:
                outl=lre.search(line)
                if(id in gene.keys()):
                        gene[id] += outl.group(1)
                else:
                        gene[id]  =outl.group(1)
~~~~~~~~

