---
aliases: [SINE Finder]
---
# SINE Finder
* [SINE Finder paper link](https://academic.oup.com/plcell/article/23/9/3117/6097673)
* the program is located in the supplemental material of the paper (the alternate download link listed (german website) doesn't work, but you can try :))
    * kind of tricky to find: 
    1. download the supp material
    2. actual python script is Supp Data File 1 (txt file)
    3. make a copy or resave this .txt file as a .py file (change file extension) so that it will be recognized as a python script
* inputs:
    * genome in fasta format (accepts .fas, .FASTA, and .mfa file extensions)
* outputs:
    * SINE sequences in fasta format

## Dependencies 
* Python 2.7

## Important notes
* ==NEED TO RUN CHUNK-WISE== ```
{ .annotate }
1. hey, did you run this chunk-wise?
 * this is why this program must be run manually- when run through the conda wrapper in Transposon Ultimate, the python recursive memory limit is exceeded for large genomes because the conda wrapper runs SINE Finder in seqwise mode, resulting in the program stopping when the memory limit is reached and subsequently incomplete annotations
    * USE EXTENSION: $ -T 'chunkwise'
* need to run with both sequence.fasta and sequence_rc.fasta because SINE finder only annotates a single strand 

## Running SINE Finder
- run in Talapas
- specifically works with python2.7 (not later versions- does some whack stuff and tries to run interactively but then immediately crashes out before any arguments are passed to the prompts, so long story short, have to specify v2.7)

1. go to directory that has sequence.fasta, sequence_rc.fasta and sine_finder.py
    ```bash
    cd sine/finder/directory
    ```
2. run command using python2.7
   ```python
   python2.7 sine_finder.py -T "chunkwise" -V -f both sequence.fasta > kim_sinefinder.out
   ```


## SINE Finder command options
```
sine_finder [options] <fastafile_name>
  OPTIONS:
     -h     (help:) display this message.
     -d     (description:) display a short description of the
            program.
     -v     (version:) print version number.
     EVALUATION PARAMETERS:
     -T (seqwise|chunkwise)
            (run type:) the way how infiles are processed (default:
            seqwise).
            'seqwise': each sequence is loaded and searched for patterns.
               For large sequences 'chunkwise' is the better choice.
            'chunkwise': only fragments (chunks) of the sequence are
               loaded and processed. The size is defined by option
               -C. To ensure that matches do not get lost by sequence
               splitting an overlap should be specified (option -O).
     -t <integer>
            TSD mismatch tolerance (default:2).
     -w <integer>
            word size TSD seed starts search with (default:5).
     -p <integer>
            penalty for a nucleotide mismatch in TSD search (default:
            1).
     -s <integer>
            TSD score cutoff (default:10).
     -o (F|R|FR)
            direction of TSD search, allowed orientation (default:F).
     (only chunkwise processing:)
     -C <integer>
            (chunksize:) size of each fragment loaded and processed
            individually. Use only when -T is set to chunkwise (default:
            100000).
     -O <integer>
            (overlap:) overlap of fragments treated by chunkwise processing.
            Use only when -T is set to chunkwise (default:8000).
     OTHER OPTIONS:
     -f (fasta|csv|both)
           (file type:) file type result is written to (default:fasta).
     -V    (verbose:) display program call.
```