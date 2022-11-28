---
aliases: [step 1]
---
# step 1 of [[a0_overall_anno_workflow|overall annotation workflow]]
**how to set up Transposon Ultimate yay**

## Transposon Ultimate annotations
- github link for reasonaTE: https://github.com/DerKevinRiehl/transposon_annotation_reasonaTE

### in & out
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

### dependencies
- Repeat masker
- repeat modeler
- conda
- python

### install reasonaTE conda environment and necessary packages
1. this could take some trial and error- I didn't have any luck using mamba to install any of the conda packages, and eventually ended up using a janky combination of the .yml environment files and conda commands
2. I would suggest just trying the .yml initially, rather than messing with the individual conda/mamba installations but do whatever
3. in the end, you just need to end up with 2 different environments- call them what you will, but they are referred to in the reasonaTE docs as **transposon_annotation_tools_env** and **transposon_annotation_reasonaTE** so that's what I used for simplicity's sake

### create project workspace on Talapas with input genome

1. run these commands on Talapas to load in the correct modules and make some folders that will hold everything for the transposon ultimate run on this genome
```python
module load python3/3.7.5
module load easybuild
module load anaconda3/2019.07

mkdir <bigfolder>
cd bigfolder/
conda activate transposon_annotation_tools_env
mkdir <workspace>
```
- replace workspace with whatever you want the overall project folder to be named

2. upload sequence fasta file to bigfolder directory
	1. all chroms in the same file
	2. make sure that the permissions are correct for the fasta: 
		```bash
		ls -l sequence.fasta
		chmod ug+rwx sequence.fasta
		chmod ug+rwx /workspace
		```
		
3. run command below to create TEUlt project (this will make a duplicate of your sequence fasta file, change the chromosome names in the duplicate fasta, get folders set up for individual programs etc) 
```python
reasonaTE -mode createProject -projectFolder <workspace> -projectName <testProject> -inputFasta <sequence.fasta>
```
- replace testProject with what you want to name the project (I'd suggest including the name of the genome being analyzed or just being mildly descriptive)
- replace sequence.fasta with the name of your input genome
	- this fasta genome file must be placed within the workspace folder you made BEFORE running the reasonaTE command (the createProject reasonaTE mode renames your fasta and also creates a reverse complement version that is needed for some of the annotation tools, so the fasta has gotta be in there initially)



