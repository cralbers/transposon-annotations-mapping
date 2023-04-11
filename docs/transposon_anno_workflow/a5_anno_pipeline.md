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

## Diagram of TEUlt pipeline 

![[TEUlt_pipeline_Riehl.png]]
From Riehl et. al. [TransposonUltimate](https://academic.oup.com/nar/article/50/11/e64/6541023) 

## TEUlt family classification codes


These codes are used to denote the family and subfamilies of a specific transposon sequence.
![[transposon_anno_workflow/TEUlt_famclassification_codes.png]]
From Riehl et. al. 
