---
aliases: [LTR Harvest]
---
# LTR Harvest
- [LTR Harvest documentation](http://genometools.org/tools/gt_ltrharvest.html)
- run locally through genometools package in specific conda env
	- [GenomeTools](http://genometools.org/index.html)
	```bash
	# create conda environment
	conda create --name envname
	# add conda channels
	conda config --add channels defaults
	conda config --add channels bioconda
	conda config --add channels conda-forge
	conda config --set channel_priority strict
	# install genome tools 
	conda install -n envname genometools-genometools
	```

## In & Out

<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome in fasta format</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">uncleaned/unfiltered LTR annotations to input into LTR Retriever</td>
    </tr>
</table>

- **use genome file that was made during TEUlt setup** (you may have to download from Talapas or copy to new directory, but **DO NOT MOVE THE ORIGINAL FILE OUT OF THE TE ULT DIRECTORY**)


## Dependencies
- genometools (conda package)
  - [genometools documentation](https://bioconda.github.io/recipes/genometools-genometools/README.html)
  - [how to install genometools](https://bioinformatics.stackexchange.com/questions/6873/how-to-install-genometools-with-anaconda)

## Running LTR Harvest 
- commands copied from [https://github.com/oushujun/LTR_retriever#inputs](https://github.com/oushujun/LTR_retriever#inputs)
1. run gt suffixerator to create necessary indices
	- [Suffixerator documentation](https://manpages.ubuntu.com/manpages/trusty/man1/gt-suffixerator.1.html)
```bash
gt suffixerator -db sequence.fasta -indexname kimcb.index -tis -suf -lcp -des -ssp -sds -dna
```

2. run gt ltrharvest to get ltr annotations in format needed for [[prgrm_LTRRet|LTR Retriever]]
```bash
gt ltrharvest -index kimcb.index -minlenltr 100 -maxlenltr 7000 -mintsd 4 -maxtsd 6 -motif TGCA -motifmis 1 -similar 85 -vic 10 -seed 20 -seqids yes -v > kimcb.harvest.scn
```

3. run gt ltrharvest to get non TGCA motif LTRs
```bash
gt ltrharvest -index kimcb.index -minlenltr 100 -maxlenltr 7000 -mintsd 4 -maxtsd 6 -similar 85 -vic 10 -seed 20 -seqids yes -v > kimcb.harvest.nonTGCA.scn
```

### command line syntax
![[ltrharvest_CLI.png]]
