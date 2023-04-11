---
aliases: [step 6]
---
# Step 6 of [overall annotation workflow](a0_overall_anno_workflow.md)
!!! info "previous step:"
    [a5_anno_pipeline](a5_anno_pipeline.md)

## Get statistics on final TE annotations (non size filtered)

- this will return statistics on the NON-SIZE filtered data
- helpful for getting an overview of the data and making sure that annotations look complete across all chromosomes

```python
conda activate transposon_annotation_reasonaTE
reasonaTE -mode statistics -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project
