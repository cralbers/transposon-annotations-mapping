---
aliases: [MUST]
---
# MUST
* ==paper link==: [(https://www.degruyter.com/document/doi/10.1515/jib-2017-0029/html?lang=en)]
- ==program download link==: [(http://www.healthinformaticslab.org/supp/resources.php)]
    * yes, this looks sketchy
    * it will be ok
    * use cmd-F and search for MUST, download the tar.gz file titled  "MUST.r2-4-002.Release.tar.gz" 
	    * if for some reason there is a more recent version, just try to get the version above because who knows what the new one looks like
- this program is a hellhole of perl scripts so sorry


## dependencies
- NCBI BLAST version 2.2.11 (version used for publication)
- BLAT version 3.5 (version used for publication)
- "open-3.3.0” version of RepeatMasker with the revision 1.250 (version used for publication)
- languages:
    - Perl
    - C/C++
    - Bash
- BioPerl

## running MUST 
- MUST is completely command line (no GUI)
- use the perl script in [[MUST_Pipe|MUST perl script]] and run in shell using some form of the command below:

```bash
./MUST_Pipe.pl <genome.fasta> <result.txt> <temp> [OPTIONS]
```

- need to run from directory that came from unzipping the MUST.tar.gz file where the MUST_Pipe.pl script is located
- if you name the output file result.txt when you run MUST, won't have to rename the file later for integration into TEUlt ([[a3_anno_combine]])
- temp is the temporary directory in which intermediary files will be stored as MUST is running, this directory needs to be initialized prior to running MUST and located within directory that holds MUST_Pipe.pl script
- CLI syntax and options (copied over from [(https://www.degruyter.com/document/doi/10.1515/jib-2017-0029/html?lang=en)]

![[MUST_CLI.png.png]]

