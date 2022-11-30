---
aliases: [LTR Harvest]
---
## LTR Harvest
- ==LTR Harvest documentation:== [(http://genometools.org/tools/gt_ltrharvest.html)]
- run locally through genometools package
	- ==genometools link==: [(http://genometools.org/index.html)]
	```bash
	# install genome tools 
	conda install -c bioconda genometools
	```
- use genome file that was made during TEUlt setup (have to download from Talapas)
	- have to do this so that all of the chromosome names are the same between the TEUlt annotations and the annotations run locally


## running LTR Harvest locally
- commands copied from [(https://github.com/oushujun/LTR_retriever#inputs)]
1. run gt suffixerator to create necessary indices
```bash
gt suffixerator -db sequence.fasta -indexname sequence.fasta.index -tis -suf -lcp -des -ssp -sds -dna
```

2. run gt ltrharvest to get ltr annotations in format needed for [[prgrm_LTRHarvest|LTR Harvest]]
```bash
gt ltrharvest -index sequence.fasta.index -minlenltr 100 -maxlenltr 7000 -mintsd 4 -maxtsd 6 -motif TGCA -motifmis 1 -similar 85 -vic 10 -seed 20 -seqids yes > sequence.fa.harvest.scn
```


