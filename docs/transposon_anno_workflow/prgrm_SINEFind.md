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

## In & Out

<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome in fasta format (accepts .fas, .FASTA, and .mfa file extensions)</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">SINE sequences in fasta format</td>
    </tr>
</table>

* **use genome file that was made during TEUlt setup** (you may have to download from Talapas or copy to new directory, but **DO NOT MOVE THE ORIGINAL FILE OUT OF THE TE ULT DIRECTORY**)

## Dependencies

* Python 2.7

## Important notes

* ==NEED TO RUN CHUNK-WISE== ```
{ .annotate }

1. hey, did you run this chunk-wise?
   * this is why this program must be run manually- when run through the conda wrapper in Transposon Ultimate, the python recursive memory limit is exceeded for large genomes because the conda wrapper runs SINE Finder in seqwise mode, resulting in the program stopping when the memory limit is reached and subsequently incomplete annotations
   * USE EXTENSION: $ -T 'chunkwise'

- need to run with both sequence.fasta and sequence_rc.fasta because SINE finder only annotates a single strand
* **use genome files that were made during TEUlt setup** (you may have to download from Talapas or copy to new directory, but **DO NOT MOVE THE ORIGINAL FILES OUT OF THE TE ULT DIRECTORY**)

## Running SINE Finder

- run in Talapas
* specifically works with python2.7 (not later versions- does some whack stuff and tries to run interactively but then immediately crashes out before any arguments are passed to the prompts, (which is very possibly user error on my part, but this was just the silly way i got it to work) so long story short, have to specify v2.7)

1. go to directory that has sequence.fasta, sequence_rc.fasta and sine_finder.py

    ```bash
    cd sine/finder/directory
    ```

2. run command using python2.7

   ```python
   python2.7 sine_finder.py -T "chunkwise" -V -f both sequence.fasta > kim_sinefinder.out
   ```

### command line syntax

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
