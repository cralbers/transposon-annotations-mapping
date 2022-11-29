---
aliases: [step 2.1]
---
# step 2.1 of [[a0_overall_anno_workflow|overall annotation workflow]]
- step 2.2: [[a2_2_anno_manual]]
!!! info "previous step:"
    [[a1_TEUlt_setup]]
- transposon ultimate annotations happen in the **transposon_annotation_tools_env** conda environment

### in & out
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


### annotate the genome using only these specific Transposon Ultimate conda packages
- helitronScanner
- mitefind
- mitetracker
- repeatmodel (RepeatModeler)
- repMasker (RepeatMasker)
- sinescan
- tirvish
- transposonPSI
- NCBICDD1000

### command to run annotations:

```python

conda activate transposon_annotation_tools_env
reasonaTE -mode annotate -projectFolder workspace -projectName testProject -tool <toolname>

```


### important notes:
- don't use the 'all' function of TEUlt in annotate mode because some of these programs didn't work and caused incomplete runs of other programs that I didn't realize were incomplete until very late
- some of the specific programs that were wrapped into conda packages for TEUlt (ie MUST v2, SINE Finder) didn't work using the conda packages, which is why I ended up running these locally and then only running specific annotation tools through the TEUlt wrapper
- run this using a Talapas job script 
	- this step will take a big long time to run all of these individual tools because of Repeatmasker and Repeatmodeler, so better to just submit the job and let  it run rather than making your poor computer do it locally

### sample Talapas job script
```bash
#!/bin/bash
#SBATCH --partition=long
#SBATCH --job-name= example
#SBATCH --output=example.out
#SBATCH --error=example.err
#SBATCH --time=0-335:59:00
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=28
#SBATCH --mail-user=email@email.edu
#SBATCH --mail-type=BEGIN,END
#SBATCH --account=accountname

module load python
module load python2/2.7.13
module load easybuild
module load GCC/6.3.0-2.27
module load OpenMPI/2.0.2
module load RepeatModeler/1.0.11
module load RepeatMasker/4.0.7
module load anaconda3/2019.07

conda activate transposon_annotation_tools_env

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool helitronScanner

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool mitefind

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool mitetracker

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool must

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool repeatmodel

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool repMasker

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool sinefind

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool sinescan

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool tirvish

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool transposonPSI

reasonaTE -mode annotate -projectFolder projectfolder -projectName projectname -tool NCBICDD1000
```





