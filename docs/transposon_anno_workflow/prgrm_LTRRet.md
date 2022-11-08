---
aliases: [LTR Retriever]
---
# LTR Retriever
* ==paper link==: https://academic.oup.com/plphys/article/176/2/1410/6117145?login=true
* ==program download link==: https://github.com/oushujun/LTR_retriever
* conda download! very easy to follow installation directions on github
* inputs:
    * genome (in fasta format) 
    * LTR RT candidates (from any combination of LTR Finder, LTRHarvest, LTR_STRUC, MGEScan 3.0.0, and LtrDetector)

## dependencies
- TRF 
- BLAST+ 
- BLAST or CD-HIT
- HMMER
- RepeatMasker

#### getting LTR RT candidates
- sufficient to use only results from LTR Finder and LTR Harvest (also the output files from these two LTR RT candidate finders do not have to be altered for input into LTR Retriever!)