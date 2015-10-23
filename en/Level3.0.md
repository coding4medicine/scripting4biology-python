# Level 3 - Regular Expressions



Searching for word is one common task in all file systems. Due to its importance, operating system developers make word search an early component of the operating system. The problem is computationally challenging, because in addition to exact words, we like to also find patterns approximately matching the lines.

We use grep -P instead of just grep to indicate that we are following PERL-like regular expression commands.

~~~~~~~~
grep -P 'pattern' filename
~~~~~~~~

1. Checking for a lettter or number

One 'a' -

~~~~~~~~
grep -P 'a' filename
~~~~~~~~

One or more 'a' -

~~~~~~~~
grep -P 'a+' filename
~~~~~~~~

Zero or more 'a' -

~~~~~~~~
grep -P 'a*' filename
~~~~~~~~

Zero or one 'a' -

~~~~~~~~
grep -P 'a?' filename
~~~~~~~~

Instead of 'a', you can pick any other letter or number. Also, the command is case sensitive. That means “grep 'a' [filename]” will give something different from “grep 'A' [filename]”.


2. Checking for a word

Looking for number of counts of 'cat' -

~~~~~~~~
grep -P 'cat' filename
~~~~~~~~

The following command looks for wildcard patterns. It searches for all words with c, some other letter and t.

~~~~~~~~
grep -P 'c.t' filename
~~~~~~~~


3.  Checking for beginning or end

Begins with a -

~~~~~~~~
grep -P '^a' filename
~~~~~~~~


Ends with a -

~~~~~~~~
grep -P 'a$' filename
~~~~~~~~


4. Checking for many letters

The following pattern looks for 'cat', 'cut' and 'cot'.

~~~~~~~~
grep -P 'c[aou]t' filename
~~~~~~~~


5. Special  \s, \S, \d, \D, \w, \W

\s  looks for a space character (could be space or tab).
\S looks for a non-space character.
\d looks for a number.
\D looks for a non-number.
\w looks for a alphabet.
\W looks for a non-alphabet.

Examples -

The following command looks for any line with number.

~~~~~~~~
grep -P '\d+' filename
~~~~~~~~

The following command looks for any line with a non-number.

~~~~~~~~
grep -P '\D+' filename
~~~~~~~~

Please note that a line with a non-number is not the same as a line not with a number.
