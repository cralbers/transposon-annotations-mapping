---
aliases: [step 6]
---
# step 6 of [[a0_overall_anno_workflow|overall annotation workflow]]
> [!previous step]
>  [[a5_anno_pipeline]]

## get statistics on final TE annotations (non size filtered)
```python
conda activate transposon_annotation_reasonaTE
reasonaTE -mode statistics -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project
