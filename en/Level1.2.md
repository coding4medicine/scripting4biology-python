# String processing


### Simple string

In python, a string is described in terms of an array (list). In the following example, x is an array. x[0]='I'. x[1]=' '. x[2]='a'.

~~~~~~~~
#!/usr/bin/env python
x='My name is Alice'
print x
~~~~~~~~

### Joining two strings

You can join two strings by using +.

~~~~~~~~
#!/usr/bin/env python
x='My name'
y=' is Alice'
print x+y
~~~~~~~~


## Splitting a string

You can also split a string by extracting part of the array.
~~~~~~~~
#!/usr/bin/env python
x='I am flying from Seattle to San Francisco'
print x[17:25]
~~~~~~~~


### Searching within a string

Here is an example of using regular expression in python. All grep-like regular expressions can be used in this example.

~~~~~~~~
#!/usr/bin/env python
import re
str = 'I am flying from Seatttle to San Francisco'
match = re.search(r'[SF]', str)
if match:
   print 'found S/F', match.group() 
else:
    print 'did not find S/F'
~~~~~~~~   

### Search and replace

The sub command replaces "Seattle" with "London" in the following example.
~~~~~~~~
#!/usr/bin/env python
import re
str = 'I am flying from Seattle to San Francisco'
x = re.sub(r'Seattle', 'London', str)
print x
~~~~~~~~

For detailed description of all regular expression rules, check here -

https://developers.google.com/edu/python/regular-expressions?hl=en


