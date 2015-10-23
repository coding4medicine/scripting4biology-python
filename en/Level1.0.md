# Level 1 - Rules of the Game


We will first learn how to write simple programs to print
short messages on the screen.

The python code is shown below. If you are using the online
tool at http://coding4medicine.com/code, you do not need
to include the first line (#!/usr/bin/env python) of the
code below. If you are testing it in a linux computer,
write the code in file (e.g. 'hello.py') using the
nano editor, save it and then run it by typing './hello.py'
from the command line.

~~~~~~~~
#!/usr/bin/env python

#
# The command 'print' is used to print a line.
#

print "Welcome to the class"

~~~~~~~~

Let me explain how the above code works. In python, the first line of the code 
starts with the '#!' sign, followed by a command that finds the location of the python 
executable in the computer.  This is the convention used by all scripting languages in
unix/linux including python, and you can simply copy the line in your new code.

The script runs by starting from the first line and continuing
line by line until reaching the end of the script. From second line
onward, if any sentence contains the character '#', all texts right of 
that character are ignored. 

The computer ignores all empty lines, and therefore, the first statement, 
where it is asked to do something, is the fifth line.  The word 'print' 
is a python instruction that tells the computer to print the following text.
If the above scrpit is run by typing -

~~~~~~~~
./hello.py
~~~~~~~~

the computer will print the message in the screen. Python adds a newline
after completing every 'print' command.


In python, the text following 'print' command can also be broken into multiple
words separated by commas.

~~~~~~~~
#!/usr/bin/env python

print "Hello, ", "my name ", "is Alice"

~~~~~~~~



