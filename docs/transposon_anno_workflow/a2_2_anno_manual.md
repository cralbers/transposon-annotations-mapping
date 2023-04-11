---
aliases: [step 2.2]
---
# Step 2.2 of [[a0_overall_anno_workflow|overall annotation workflow]]

- Step 2.1: [[a2_1_anno_TEUlt]]

!!! info "previous step:"
    [[a1_TEUlt_setup]]

!!! warning "IMPORTANT"
	- these local annotations should be run with the sequence.fasta (and sequence_rc.fasta if needed) file that was generated during the TEUlt setup process ([[a1_TEUlt_setup|step 1]]) to ensure that the chromosome naming is the same across all files
	- if the chromosome naming is inconsistent, the TEUlt pipeline ([[a5_anno_pipeline|step 5]]) will not run correctly

## Local/manual annotations

- [ ] [[prgrm_MUST|MUST]]

- [ ] [[prgrm_LTRRet|LTR Retriever]]

- [ ] [[prgrm_SINEFind|SINE Finder]]

- [ ] [[prgrm_LTRHarvest|LTR Harvest]]

- [ ] [[prgrm_LTRFinder|LTR Finder]]

## Approximate runtimes 

| program | time | computer |
| ---- | ---- |---- |
| MUST | ~100 min | Talapas |
| LTR Finder parallel | ~5 min | Talapas |
| LTR Harvest | ~90 min | local |
| LTR Retriever | ? | Talapas |
|SINE Finder | ~5 min | Talapas |

* LTR Harvest runtimes are really variable- runs in like 10 seconds on Libuda CB but literally took  and hour and a half for the Kim CB, and won't even run for nonTGCA motifs on Kim CB (according to the paper, the program run time is really dependent on how repetitive the genome is)