---
aliases: [step 2.1]
---
# step 2.1 of [[a0_overall_anno_workflow|overall annotation workflow]]
- step 2.2: [[a2_2_anno_manual]]
> [!previous step]
> [[a1_TEUlt_setup]]
- transposon ultimate annotations happen in the **transposon_annotation_tools_env** conda environment

### in & out:
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





