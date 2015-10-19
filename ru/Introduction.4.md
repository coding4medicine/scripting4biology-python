# Biological questions for this course

The purpose of this course is to teach you programming using examples from common biological problems. Please answer these
questions without using any Bio-related library like bioperl or biopython.  Use danio-genes.fasta sequence file for Q1-2 and 
ecoli-genome.fasta sequence file for Q3-5.

## Q1. Reverse Complement



## Q2. Translating nucleotide sequences to into protein sequences



## Q3. Computing GC-content of a genome

A genome sequence consists of four types of nucleotides (A, T, G, C). Often it may also include N to represent the unsequenced bases. The GC content of a genome means the ratio of the number of G/C bases and the number of A/T/G/C bases.

Write a program to compute the GC-content of the E. coli genome.

## Q4. Kmer statistics of a genome

In this problem, you need to identify k-mer statistics of the E. coli genome for k=21. The concept of k-mer statistics is explained below.

You can split a genome sequence or any other long nucleotide sequence into short overlapping ‘kmers’. For example, the sequence ‘ATGCTGGAAAT’ can be split into the following 3-mers: ATG, TGC, GCT, CTG, TGG, GGA, GAA, AAA, AAT. Similarly, if you choose k=4, you get the following 4-mers: ATGC, TGCT, GCTG, CTGG, TGGA, GGAA, GAAA, AAAT. In each case, you also need to consider the reverse strand by taking reverse complement of the entire sequence, and that gives you
another set of k-mers.

Some k-mer may appear multiple times within a genome or a long sequence. Therefore, ‘k-mer statistics’ of genome is a table with the sequences of the k-mers and the their corresponding counts.

As an example, the k-mer (k=3) statistics of AAAAAAAA is - (AAA 6 times and TTT 6 times) after including both strands.
Introductory test 12

## Q5. Locating RNase P RNA in a genome

Ribonucleade P (RNase P) RNA is an ancient RNA just like tRNA or ribosomal RNA. It is present in the genomes of almost all living species. Unfortunately, the sequence of this RNA changes so much from organism to organism that programs like BLAST cannot find it. The only way to find them is to look for some conserved motifs (patterns) present in all RNase P.

In bacteria, RNase P RNA can be identified by searching for the following two conserved sequences in close proximity (i.e. within less than 600 nt.) (Li, Altman 2004).

1. GAGGAANNTCNNNNC
2. (AGNNNNAT…{10–60 nt}…ACANAANNNNGNNUA)
N above means any of A,T,G,C.
Write a script to locate RNaseP RNA within the E. coli genome.
