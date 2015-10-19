# Module 6 - Complex Programs

## Computing GC-content

~~~~~~~~
#!/usr/bin/python3

import sys, re

f=open(sys.argv[-1],'r')
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



## K-mer counting



~~~~~~~
#!/usr/bin/python3

import sys, re

f=open(sys.argv[-1],'r')
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


print(gene)

f=open('num','r')
lines=f.readlines()

for x in lines:
        y=int(x)
        print y+1

~~~~~~~


~~~~~~~
#!/usr/bin/python3

import sys, re

f=open(sys.argv[-1],'r')
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


print(gene)

f=open('num','r')
lines=f.readlines()

for x in lines:
        y=int(x)
        print y+1
~~~~~~~

## Translating nucleotides into proteins



~~~~~~~~
#!/usr/bin/python3

T={'TTT':'F', 'TTC':'F', 'TTA':'L', 'TTG':'L', 'TCT':'S', 'TCC':'S', 'TCA':'S', 'TCG':'S', 
'TAT':'Y', 'TAC':'Y', 'TAA':'STOP', 'TAG':'STOP', 'TGT':'C', 'TGC':'C', 'TGA':'STOP', 'TGG':'W', 
'CTT':'L', 'CTC':'L', 'CTA':'L', 'CTG':'L', 'CCT':'P', 'CCC':'P', 'CCA':'P', 'CCG':'P', 'CAT':'H', 
'CAC':'H', 'CAA':'Q', 'CAG':'Q', 'CGT':'R', 'CGC':'R', 'CGA':'R','CGG':'R',
'ATT':'I','ATC':'I','ATA':'I','ATG':'M','ACT':'T','ACC':'T','ACA':'T','ACG':'T',
'AAT':'N','AAC':'N','AAA':'K','AAG':'K','AGT':'S','AGC':'S','AGA':'R','AGG':'R',
'GTT':'V','GTG':'V','GTA':'V','GTG':'V','GCT':'A','GCC':'A','GCA':'A','GCG':'A',
'GAT':'D','GAC':'D','GAA':'E','GAG':'E','GGT':'G','GGC':'G','GGC':'G','GGA':'G','GGG':'G'};

f=open('gene','r')
line=f.readline()
i=0

while(i<1000):
        x = line[i:i+3]
        print T[x],
        i=i+3
~~~~~~~~


## Finding RNase P RNA
