# Level 5 - An example of full program



## Reading a FASTA file


A FASTA file has the following format -

~~~~~~~~
>ID1
ATGTGGGAGG
AAGGTGGGTG
AAA
>ID2
AAAATGTGTGTGG
AAAT

>ID3 (gene pd1, discovered 2001)
ATGGTGATA
TTTTTTTTTTTTTTT
AAAATGTGTGT
~~~~~~~~


Described in text, a fasta file reports the ID and sequence of each gene. The ID line starts with '>' and may have additional text following the identifier. The sequence can be split into multiple lines. There can be empty sentences in between two genes.

How do we write a script to read a FASTA file and use it for other analysis? This is a fascinating example covering many different aspects of programming.


## Data structure

The first question is what type of data structure we should use to store the FASTA file. Data structure is the method to store data within your program. For individual data, you can hold in string, integer or decimal data structure. For collection of data, you need something like array or associative array. Graph is a possible data structure for data on Airplanes flying between cities.

As you continue to write more and more programs, you will realize that the data structure question becomes very important in your work. In fact, it is one of the two major components of programming, the other one being algorithm. After you master a language, you will find the language to be of less importance in day to day work.

Getting back to data structure question, it is clear that you can use string format to hold each gene or protein sequence. For the collection of genes, you need to use something like an array. In fact, you will need two arrays – one to store the ID and the other to hold the sequence. So, the format  is  ID_array[0]='ID1' and seq_array[0]='ATGTGGGAGGAAGGTGGGTGAAA', and so on.

Is that the best data structure? You can answer only by thinking about what kind of questions you will have to answer in your program. In bioinformatics, often you will come across questions like 'what is the sequence of gene ID2?' To answer that, you will have to first go over the entire ID_array to find the coordinate of gene ID2 and then you go to seq_array to find its sequence. That entire process is time-consuming and you need a better data structure to answer the question very rapidly. 

An associative array becomes a better answer in this case. In case of associative array, you will need only one array, whose identifiers are FASTA Ids and values are sequences. It will look like  fasta_array['ID1']='ATGTGGGAGGAAGGTGGGTGAAA', and so on for the rest of the genes.

In our program, we will use associative arrays.


## PERL


In PERL, a string is described as a variable.

~~~~~~~~
#!/usr/bin/perl

#####################
# code to read FASTA file
#####################

open( IN, "genes.fasta");
while(<IN>)
{
    if($_=~/^>(\S+)/)
    {
           $ID=$1;
    }
    else
     {
        if($_=~/(\S+)/)
        {
          $fasta_array{$ID} .=$1;
         }
     }
}
~~~~~~~~

Let me explain in words, what the program is doing. It reads the file 'genes.fasta'. Then it goes over each line and checks whether the line starts with '>'. If the line starts with that character, the non-space letters following '>' are recognized as ID. If the line does not start with that character, its non-space content is added to the associative array line for the corresponding ID.

Please review the above code and then try to write your own version.



## PYTHON

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

## GO

~~~~~~~~
// https://gobyexample.com/regular-expressions

package main
import ("bufio"
        "fmt"
        "os"
        "regexp")

func main() {
        file,err := os.Open("file.fa")
        if(err !=nil) {}

        scanner := bufio.NewScanner(file)

        for scanner.Scan() {
                fmt.Println(scanner.Text())

                match, _ := regexp.Compile('^>\S+')

                if(match) {
                                fmt.Println(scanner.Text())
                }
        }
}
~~~~~~~~

Let me explain in words, what the program is doing. It reads the file 'genes.fasta' in an array. Then it goes over each line and checks whether the line starts with '>'. If the line starts with that character, the non-space letters following '>' are recognized as ID. If the line does not start with that character, its non-space content is added to the associative array line for the corresponding ID.

Please review the above code and then try to write your own version.


