---
aliases: [step 5]
---
# step 5 of [[a0_overall_anno_workflow|overall annotation workflow]]
!!! info "previous step:"
    [[a4_anno_parse]]

- now that all the annotations are in the same format, can run the TEUlt pipeline which runs duplicate filter, CDHIT, BLASTN and then the copy filter

```python
conda activate transposon_annotation_reasonaTE
reasonaTE -mode pipeline -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project
