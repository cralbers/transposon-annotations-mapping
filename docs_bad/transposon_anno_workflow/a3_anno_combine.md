---
aliases: [step 3]
---
# Step 3 of [[a0_overall_anno_workflow|overall annotation workflow]]
!!! info "previous step:"
    [[a2_1_anno_TEUlt]] 
    [[a2_2_anno_manual]]

---
- at this stage, have to combine output files from any programs you ran locally into wherever you have compiled and are running TEUlt and the two conda environments
- this is pretty easy, there are just some naming conventions that have to be followed for each specific program, because the TEUlt scripts have hardcoded in some specific filenames to look for within the larger workspace folder system and it won't recognize other files as annotations to parse if they aren't named correctly

program | file to get from outputs | rename to this | program info
------------ | ------------ | ------------ | ------------
LTR Retriever | ~.pass.list.gff3 | just needs to end with .gff3 | [[a2_2_anno_manual#LTR Retriever]]
MUST | the only output file | result.txt | [[a2_2_anno_manual#MUST]]
SineFinder | sequence-matches.fasta | sequence-matches.fasta | [[a2_2_anno_manual#SINE Finder]]

## Check annotation imports
in order to check that all of the files from programs you ran manually/locally were input into the TEUlt project folder correctly, can run annotation check command
```python
conda activate transposon_annotation_tools_env
reasonaTE -mode checkAnnotations -projectFolder workspace -projectName testProject
```
- anything that is marked as completed will be considered by the rest of the pipeline