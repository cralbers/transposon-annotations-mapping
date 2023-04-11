---
aliases: [MUST]
---
# MUST
* [MUST paper link](https://www.degruyter.com/document/doi/10.1515/jib-2017-0029/html?lang=en)
- [MUST download link](http://www.healthinformaticslab.org/supp/resources.php)
    * yes, this looks sketchy
    * it will be ok
    * use cmd-F and search for MUST, download the tar.gz file titled  "MUST.r2-4-002.Release.tar.gz" 
	    * if for some reason there is a more recent version, just try to get the version above because who knows what the new one looks like
- this program is a hellhole of perl scripts so sorry

## In & Out

<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome in fasta format</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">MITE annotations (result.txt)</td>
    </tr>
</table>

- **use genome file that was made during TEUlt setup** (you may have to download from Talapas or copy to new directory, but **DO NOT MOVE THE ORIGINAL FILE OUT OF THE TE ULT DIRECTORY**)
- this is how the MUST directory needs to be structured ```
```
genome_MUST_dir
|- MUST_talapas_script.sh
|- MUST.r2-4-002.Release/     # unzipped MUST tar.gz 
| |- sequence.fasta
| |- MUST_Pipe.pl
| |- temp/
```

## Dependencies
- NCBI BLAST version 2.2.11 (version used for publication)
- BLAT version 3.5 (version used for publication)
- "open-3.3.0” version of RepeatMasker with the revision 1.250 (version used for publication)
- languages:
    - Perl
    - C/C++
    - Bash
- BioPerl

## Running MUST 
- run on Talapas, this will take a couple hours so best to not run locally
  - example script for running on Talapas in code folder [[kim_must_talapas.sh]]
- MUST is completely command line (no GUI)
- use the perl script (in [[MUST_Pipe|MUST perl script]]) and run in shell using some form of the command below:

```bash
./MUST_Pipe.pl <genome.fasta> <result.txt> <temp> [OPTIONS]
```


- need to run from directory that came from unzipping the MUST.tar.gz file where the MUST_Pipe.pl script is located
- if you name the output file result.txt when you run MUST, won't have to rename the file later for integration into TEUlt ([[a3_anno_combine]])
- temp is the temporary directory in which intermediary files will be stored as MUST is running
	- this directory needs to be created prior to running MUST and located within directory that holds MUST_Pipe.pl script

### command line syntax
| ![[MUST_CLI.png.png]] |
|:--:|
| <b>MUST CLI syntax and options</b> (copied over from [https://www.degruyter.com/document/doi/10.1515/jib-2017-0029/html?lang=en](https://www.degruyter.com/document/doi/10.1515/jib-2017-0029/html?lang=en)|


