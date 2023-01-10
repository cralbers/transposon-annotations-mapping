---
aliases: [step 5]
---
# Step 5 of [[a0_overall_anno_workflow|overall annotation workflow]]
!!! info "previous step:"
    [[a4_anno_parse]]

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
From Riehl et. al. [(https://academic.oup.com/nar/article/50/11/e64/6541023)] \\
![[TEUlt_pipeline_Riehl.png]]

## TEUlt family classification codes
From Riehl et. al. \\
These codes are used to denote the family and subfamilies of a specific transposon sequence.
![[transposon_anno_workflow/TEUlt_famclassification_codes.png]]
