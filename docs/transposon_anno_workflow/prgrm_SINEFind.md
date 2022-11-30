---
aliases: [SINE Finder]
---
# SINE Finder
* ==paper link==: [(https://academic.oup.com/plcell/article/23/9/3117/6097673)]
* the program is located in the supplemental material of the paper (the alternate download link listed (german website) doesn't work, but you can try :))
    * kind of tricky to find: 
    1. download the supp material
    2. actual python script is Supp Data File 1 (txt file)
    3. make a copy or resave this .txt file as a .py file so that it will be recognized as a python script
* inputs:
    * genome in fasta format (accepts .fas, .FASTA, and .mfa file extensions)
* outputs:
    * SINE sequences in fasta format

## dependencies 
* Python (minimum v2.5)

## important notes
* ==NEED TO RUN CHUNK-WISE== ```
{ .annotate }
1. hey, did you run this chunk-wise?
 * this is why this program must be run manually- when run through the conda wrapper in Transposon Ultimate, the python recursive memory limit is exceeded for large genomes because the conda wrapper runs SINE Finder in seqwise mode, resulting in the program stopping when the memory limit is reached and subsequently incomplete annotations
    * USE EXTENSION: $ -T 'chunkwise'