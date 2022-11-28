---
aliases: [step 4]
---
# step 4 of [[a0_overall_anno_workflow|overall annotation workflow]]
> [!previous step]
>  [[a3_anno_combine]]

- need to parse annotations so that they are all in the same format and can be used in the rest of the pipeline
- annotation parsing happens in the **transposon_annotation_tools_env** conda environment

### run annotation parsing
```python
conda activate transposon_annotation_tools_env
reasonaTE -mode parseAnnotations -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project

### check the status of annotation parsing
```python
conda activate transposon_annotation_tools_env
reasonaTE -mode checkParsed -projectFolder workspace -projectName testProject
```
- replace workspace with the name of your workspace
- replace testProject with the name of your project
