---
aliases: [overall annotation workflow]
---
# ANNOTATIONS
---
these notes are located at https://cralbers.github.io/transposon-annotations-mapping/

## annotation workflow
major steps of the transposon annotation and tracking workflow i used because my file organization is absolutely horrific and I want to learn how to use this obsidian program and also apparently i am accountable for what i did lol.

- all of the individual functions that are defined within the TEUlt are explained here -> [[TEUlt_file_fxs]]
- changes to integrate LTR Retriever -> [[LTRRet_integration]]
- other random changes to source code -> [[other_source_changes]]

## 
``` mermaid 
graph TD
	F(TEUlt setup) --> A;
	F(TEUlt setup) --> B;
	A(TEUlt annotations) -->C(Transposon Annotation);
	B(Manual Annotations) -->C(Transposon Annotation);
	C --> D(Combine Annotations);
	D --> E(Parse Annotations);
	E --> G(Run TEUlt Pipeline);
	G --> H(Annotation Stats);
	G --> I(Size Filtering);
	I --> J(Visualize);

```




## individual steps
1. [[a1_TEUlt_setup]]
2. annotation of transposons
	1. [[a2_1_anno_TEUlt]] (annotate genome using Transposon Ultimate)
	2. [[a2_2_anno_manual]] (annotate genome with local/manual tools)
3. [[a3_anno_combine]] (combine the TEUlt and local/manual transposon annotations)
4. [[a4_anno_parse]] (get all TE annotations into a common file format)
5. [[a5_anno_pipeline]] (run the TEUlt pipeline on all of the TE annotations
6. [[a6_anno_stats]] (get stats on the ==non-size filtered data== that was output by TEUlt)
7. [[a7_size_filter]] (filter out massive TEs that were annotated but no possible way they are actual TEs)
8. [[a8_make_pictures]] (make some graphs of the data and other data exploration fxns)
