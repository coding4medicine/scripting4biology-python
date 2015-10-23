# On Programming and Programming Languages

## On programming

Computer programming involves writing the steps for solving a problem in such a way that a computer can repeat the 
tasks for many sets of data without any human intervention. Programming involves taking care of three aspects -
programming language, algorithm and data structure. 

Often new bioinformaticians ask which programming languange is the best for bioinformatics. Such questions tend to distract one 
from the fact that the biggest effort in solving a problem is spent on understanding the scientific question and in designing 
appropriate algorithms and data structure. Those, who do such tasks well, are usually not constrained by the specifics of 
various programming languages. Moreover, programming languages themselves are evolving, and each one incorporates bright ideas 
popularized by others at a rapid pace.


## Proliferation of programming languages

If any language can be used to solve any computing problem, why are there so many? The reason for proliferation of programming languages
is not too different from the reason for existence of myriads of human languages. Each programming language was initially adopted by 
a small community to solve certain specific computing tasks.  Subsequently, new features were added to some of those languages and 
new users started to use them. Over time, some languages evolved to find widespread use, whereas many others did not survive in 
the race to be among the fittest.

Computers are binary machines.  The only 'programming language' they understand contains two 'commands' - 0 and 1. Although such 
binary language is easy for computers, it is extremely difficult for human programmers. So the need arose for human-like languages. 
However, any human-like code needs to be ultimately translated to 0s and 1s, and therefore a programming language providing closest 
abstraction of hardware can be converted most efficiently.  The proliferation of languages over the last 50 years was related to 
balancing of two aspects - ease of human understandability and ease of translation into hardware code.

## Evolution of programming languages - C, C++, PERL, python and GO

Program --> compiler --> 0/1

Computers became even faster allowing room for another level of abstraction--> R (1993)

The above code fragment is talking about moving numbers between the RAM and registers in ALU, and performing various arithmetic/logical operations on the numbers in various registers.  Every other code, from C++ to python, needs to be converted to the above form (assembly language) before the ALU can understand and execute it.

All programs written in C, C++ and Java need to be 'compiled' so that human-readable form (English text) gets translated to a form understood by computers (0s and 1s). Usually, the step of compilation is done separately prior to running the programs on real data. Morever, programs written in C, C++ and Java have to follow very rigid structure so that the compilation process produces the most efficient code. Those sequence of steps were helpful, if computers were used for solving large problems, but were quite inefficient for using computers to do some quick and dirty work (such as removing the first column of a large table).

Thanks to Moore's law, computers became quite powerful by early 1990s making room for little bit of sloppiness in programming.
PERL came from UNIX shell programming. (1989)
Python came from C. (1989)
They do not need to be compiled. --> Interpreted.

## Scripting language

A program executes from top to bottom.


## How to learn a new programming language?

Find the codes for -

a) How to run a simple code - Module1

b) How to do simple calculations (numbers and variables) - Module1

c) How to do repetitive calculations (loops and conditions) - Module1

d) How to read from and write into files -Module4

e) How to use arrays or lists - Module1

f) How to process strings and associative arrays - Module1, Module1

g) How to reuse code (functions, modules, packages, libraries, etc.) - Module7, Module8



## Algorithm and data structure

Data structure - Only one possible - a large memory block. The rest are all abstractions.

## How to debug a program?

1. Google the error message

2. Convert the problem into smaller problem

3. Identify the exact location of error (both in code and data)

