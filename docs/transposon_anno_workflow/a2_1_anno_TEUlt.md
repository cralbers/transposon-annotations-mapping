---
aliases: [step 2.1]
---
# Step 2.1 of [overall annotation workflow](a0_overall_anno_workflow.md)

- Step 2.2: [a2_2_anno_TEUlt](a2_2_anno_TEUlt.md)

!!! info "previous step:"
    [a1_TEUlt_setup](a1_TEUlt_setup.md)
    
- transposon ultimate annotations happen in the **transposon_annotation_tools_env** conda environment

### In & Out
<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">genome fasta that should already be set up in the TEUlt workspace made in <a href="1_TEUlt_setup.md" class="internal-link">step 1</a></td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">individual tool folders in TEUlt workspace populated with respective outputs of each individual annotation tool</td>
    </tr>
</table>


### Annotate the genome using only these specific Transposon Ultimate conda packages
- helitronScanner
- mitefind
- mitetracker
- repeatmodel (RepeatModeler)
- repMasker (RepeatMasker)
- sinescan
- tirvish
- transposonPSI
- NCBICDD1000

### Command to run annotations:
- in theory, could run each of these tools individually and locally, using your own computer's resources but that would probably take forever, so it's better to just pop this command into a slurm script and run it from Talapas
- running all of these tools in Talapas took ~27 hours, do with that what you will

```python

conda activate transposon_annotation_tools_env
reasonaTE -mode annotate -projectFolder workspace -projectName testProject -tool <toolname>

```


### Important notes
- don't use the 'all' function of TEUlt in annotate mode because some of these programs didn't work and caused incomplete runs of other programs that I didn't realize were incomplete until very late
- some of the specific programs that were wrapped into conda packages for TEUlt (ie MUST v2, SINE Finder) didn't work using the conda packages, which is why I ended up running these locally and then only running specific annotation tools through the TEUlt wrapper
- run this using a Talapas job script 
	- this step will take a big long time to run all of these individual tools because of Repeatmasker and Repeatmodeler, so better to just submit the job and let  it run rather than making your poor computer do it locally
    - sample Talapas job script in [code](index.md) folder 

