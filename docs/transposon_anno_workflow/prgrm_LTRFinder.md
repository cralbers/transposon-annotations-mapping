---
aliases: [LTR Finder]
---
# LTR Finder

- [LTR Finder paper link](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1933203/)
- [LTR Finder github](https://github.com/xzhub/LTR_Finder)
- [LTR Finder parallel paper link](https://mobilednajournal.biomedcentral.com/articles/10.1186/s13100-019-0193-0)
- [LTR Finder parallel github](https://github.com/oushujun/LTR_FINDER_parallel)

## LTR Finder parallel
### What is it?
- perl wrapper for LTR Finder
- splits chromosomes into 1Mb segments and then runs LTR Finder on all segments in parallel
- uses timeout mechanism so that complicated regions are further split if LTR Finder is taking too long on one segment

### Why use it?
- the original LTR Finder runs sequentially, so is very slow on large genomes
- LTR Finder frequently used on plant genomes, which are large and also contain massive amounts of LTRs and transposons overall, meaning that this program took forever (1.16 years for the 14.5 Gb bread wheat genome)
- parallelization of LTR Finder resulted in up to 8500X faster identification of LTRs


## Running LTR Finder parallel
- run on Talapas
  - example script for running on Talapas in code folder [[kim_ltrfinder_parallel_talapas.sh]]


```bash
perl LTR_FINDER_parallel -harvest_out -seq sequence.fasta 
```