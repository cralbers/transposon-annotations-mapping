---
aliases: [step 1]
---
# step 1 of [[a0_overall_anno_workflow|overall annotation workflow]]
**how to set up Transposon Ultimate yay**

## Transposon Ultimate annotations
- github link for reasonaTE: https://github.com/DerKevinRiehl/transposon_annotation_reasonaTE

### in & out:
<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome in fasta format</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">a ton of gff3 files in a great folder organization system (except if you have to run TEUlt on multiple different genomes, all the file names will be the same which is irritating that it doesn't name the outputs based on the input fasta name but whatever, just make sure you rename your stuff if doing multiple genomes)</td>
    </tr>
</table>

### dependencies:
- Repeat masker
- repeat modeler
- conda
- python

### install reasonaTE conda environment and necessary packages
1. this could take some trial and error- I didn't have any luck using mamba to install any of the conda packages, and eventually ended up using a janky combination of the .yml environment files and conda commands
2. I would suggest just trying the .yml initially, rather than messing with the individual conda/mamba installations but do whatever
3. in the end, you just need to end up with 2 different environments- call them what you will, but they are referred to in the reasonaTE docs as **transposon_annotation_tools_env** and **transposon_annotation_reasonaTE** so that's what I used for simplicity's sake

### create project workspace on Talapas with input genome
```python
conda activate transposon_annotation_tools_env
mkdir <workspace>
reasonaTE -mode createProject -projectFolder <workspace> -projectName <testProject> -inputFasta <sequence.fasta>
```
- replace workspace with whatever you want the overall project folder to be named
- replace testProject with what you want to name the project (I'd suggest something about including the name of the genome being analyzed)
- replace sequence.fasta with the name of your input genome
	- this fasta genome file must be placed within the workspace folder you made BEFORE running the reasonaTE command- the createProject reasonaTE mode renames your fasta and also creates a reverse complement version that is needed for some of the annotation tools, so the fasta has gotta be in there initially



