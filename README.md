# test-repo

##README
Kurt
March 5, 2025
Computing for Biology: Week 8 Assignment

**dnacalc.py with the two additions**
> Below is the code for the entire new dnacalc.py program. The line allowing you to enter your own DNA sequence is commented out for now so the example remains; if you want to input your own sequence, remove the hashtag and enter one in front of the sample DNASeq variable in the line above.

`#!/usr/bin/env python3
#This program gives the length and nucleotide composition of a given DNA sequence.

#DNASeq = "ATCTCTCATTCAAAGCA"
DNASeq = input("Enter a DNA sequence here: ")
DNASeq = DNASeq.replace(" ","")
DNASeq = DNASeq.upper()
if "U" in DNASeq:
        print ("You have entered an RNA sequence instead of a DNA sequence. Each uracil nucleotide will be replaced with a thymine nucleotide.")
        DNASeq = DNASeq.replace("U","T")
#The lines above remove unnecessary spaces, auto-capitalizes any letters, and converts any uracil nucleotides to thymine nucleotides.

print ('Sequence:', DNASeq)
#Repeats the sequence provided.

SeqLength = float(len(DNASeq))
print ('Sequence length:', SeqLength)
#Provides the sequence length and sets it as a floating-point variable.

NumberA = DNASeq.count('A')
NumberC = DNASeq.count('C')
NumberG = DNASeq.count('G')
NumberT = DNASeq.count('T')
#Counts the number of each nucleotide in the sequence and establishes them as variables.

SeqLength = float(len(DNASeq))
print ('A: %.1f' % (100 * NumberA/SeqLength))
print ('C: %.1f' % (100 * NumberC/SeqLength))
print ('G: %.1f' % (100 * NumberG/SeqLength))
print ('T: %.1f' % (100 * NumberT/SeqLength))
#Takes the percentages of each sequence.

TotalStrong = NumberG + NumberC
TotalWeak = NumberA + NumberT
#Takes the sum of each complementary nucleotides to be used in calculating the melting temperature of the DNA sequence.

if SeqLength >= 14:        MeltTempLong = 64.9 + 41 * (TotalStrong - 16.4) / SeqLength
        print ("Melting temperature (long sequence): %.1f°C" % (MeltTempLong))
else:
        MeltTemp = (4 * TotalStrong) + (2 * TotalWeak)
        print ("Melting temperature (short sequence): %.1f°C" % (MeltTemp))
#Calculating the melting temperature.`

**Inputs and Outputs**
> Except for the first sample, using the example DNA sequence from the textbook, all of the input sequences below have the # removed from the "Enter a sequence" line and replaced in front of the example. 

Textbook example:
`kurt@Kurts-Laptop:~$ ./dnacalc.py
Sequence: ATCTCTCATTCAAAGCA
Sequence length: 17.0
A: 35.3
C: 29.4
G: 5.9
T: 29.4
Melting temperature (long sequence): 39.8°C`

Short DNA sequence:
`kurt@Kurts-Laptop:~$ ./dnacalc.py
Enter a DNA sequence here: ATCG
Sequence: ATCG
Sequence length: 4.0
A: 25.0
C: 25.0
G: 25.0
T: 25.0
Melting temperature (short sequence): 12.0°C`

Short RNA Sequence:
`kurt@Kurts-Laptop:~$ ./dnacalc.py
Enter a DNA sequence here: AUCG
You have entered an RNA sequence instead of a DNA sequence. Each uracil nucleotide will be replaced with a thymine nucleotide.
Sequence: ATCG
Sequence length: 4.0
A: 25.0
C: 25.0
G: 25.0
T: 25.0
Melting temperature (short sequence): 12.0°C`

Long DNA Sequence:
`Enter a DNA sequence here: ATCGATCGATCCAAGG
Sequence: ATCGATCGATCCAAGG
Sequence length: 16.0
A: 31.2
C: 25.0
G: 25.0
T: 18.8
Melting temperature (long sequence): 43.4°C`

Long RNA Sequence:
kurt@Kurts-Laptop:~$ ./dnacalc.py
Enter a DNA sequence here: AUUUCGCAAUCGACUUCAGAACU
You have entered an RNA sequence instead of a DNA sequence. Each uracil nucleotide will be replaced with a thymine nucleotide.
Sequence: ATTTCGCAATCGACTTCAGAACT
Sequence length: 23.0
A: 30.4
C: 26.1
G: 13.0
T: 30.4
Melting temperature (long sequence): 51.7°C`
