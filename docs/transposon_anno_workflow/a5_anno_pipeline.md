---
aliases: [step 5]
---
# Step 5 of [overall annotation workflow](a0_overall_anno_workflow.md)
!!! info "previous step:"
    [a4_anno_parse](a4_anno_parse.md)

## In & Out
<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">TE annotations from all of the individual annotation tools</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black"> annotations without size filtering </td>
    </tr>
</table>

## Run TEUlt Pipeline
- now that all the annotations are in the same format, can run the TEUlt pipeline which runs the duplicate filter, CDHIT, BLASTN and then the copy filter

```python
conda activate transposon_annotation_reasonaTE
reasonaTE -mode pipeline -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project

## Annotation output format
The output files are formatted according to the standard gff3 format which is documented here -> [gff3 format](https://useast.ensembl.org/info/website/upload/gff3.html)

column | title | description
---- | ---- | ----
1 | sequence id | name of the chromosome
2 | source | name of the program the annotation came from (for TEUlt, when all the annotations are consolidated, the individual program names are removed and all annotations are listed as sources from reasonaTE)
3 | type | what the annotation feature is 
4 | start | start position of the annotation
5 | stop | end position of the annotation
6 | score | depends on the individual program annotation is from
7 | strand | + for forward and - for reverse
8 | phase | indicates the first base of the annotation that is the first base of a codon (will be a "." for TEUlt because codons weren't analyzed)
9 | description | other descriptors that were added by individual programs 

## Diagram of TEUlt pipeline 

![[TEUlt_pipeline_Riehl.png]]
From Riehl et. al. [TransposonUltimate](https://academic.oup.com/nar/article/50/11/e64/6541023) 

## TEUlt family classification codes


These codes are used to denote the family and subfamilies of a specific transposon sequence.
![[transposon_anno_workflow/TEUlt_famclassification_codes.png]]
From Riehl et. al. 
