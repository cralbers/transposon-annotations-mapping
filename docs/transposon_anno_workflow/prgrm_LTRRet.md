---
aliases: [LTR Retriever]
---
# LTR Retriever
* [LTR Retriever paper link](https://academic.oup.com/plphys/article/176/2/1410/6117145?login=true)
* [LTR Retriever download link](https://github.com/oushujun/LTR_retriever)
* conda download! very easy to follow installation directions on github

## In & Out

<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome in fasta format, LTR RT candidates (from any combination of LTR Finder, LTRHarvest, LTR_STRUC, MGEScan 3.0.0, and LtrDetector)</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">filtered and parsed LTR annotations</td>
    </tr>
</table>

- **use genome file that was made during TEUlt setup** (you may have to download from Talapas or copy to new directory, but **DO NOT MOVE THE ORIGINAL FILE OUT OF THE TE ULT DIRECTORY**)

## Dependencies
- TRF 
- BLAST+ 
- BLAST or CD-HIT
- HMMER
- RepeatMasker

## getting LTR RT candidates
1. it is sufficient to use only results from [[prgrm_LTRFinder|LTR Finder]] and [[prgrm_LTRHarvest|LTR Harvest]] (pro tip: the output files from these two LTR RT candidate finders do not have to be altered for input into LTR Retriever!)
2. create a new directory (calling this ltrret_dir for the rest of this) (doesn't really matter where at this point) and copy over the following files:
	- **from LTR Harvest:** sequence.fa.harvest.scn and sequence.fa.harvest.nonTGCA.scn (if you decide to create/use this file for the non TGCA motif option in LTR Retriever)
	- **from LTR Finder:** sequence.fasta.finder.combine.scn
	- **genome file:** sequence.fasta
3. use command below to combine LTR Finder and LTR Harvest annotations into one file
	```bash
cat sequence.fa.harvest.scn sequence.fasta.finder.combine.scn > sequence.fa.rawLTR.scn
	```
4. upload ltrret_dir directory to Talapas
5. upload the LTR Retriever code folder to ltrret_dir
6. use command below to run LTR Retriever 
	- example script for running on Talapas in code folder ([[kimltrret.sh]])
	- need to make sure that ug has rwx permissions for the LTR_Retriever executable in the LTR Retriever code folder before submitting batch job (it won't work to just give rwx to the LTR Retriever code directory, you've gotta specify the executable directly or else it gets mad and says Permission Denied)
	```bash
	chmod ug+rwx ~/LTR_retriever/LTR_retriever
	```

```bash
/home/calbers/libudalab/kim_ltrretriever/LTR_retriever/LTR_retriever -genome sequence.fasta -inharvest genome.fa.rawLTR.scn -verbose -u .0000002808 > kim_LTR_retriever.out
```