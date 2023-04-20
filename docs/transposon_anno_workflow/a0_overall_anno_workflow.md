---
aliases: [overall annotation workflow]
---
# ANNOTATIONS
---

## Annotation workflow
These are the major steps of the transposon annotation and tracking workflow I used to generate the TE annotations. 

!!! example
	Transposon Ultimate is referred to as TEUlt throughout this site.

	[TEUlt paper](https://academic.oup.com/nar/article/50/11/e64/6541023?login=true)
	
	[TEUlt github](https://github.com/DerKevinRiehl/TransposonUltimate)

- all of the individual functions that are defined within the TEUlt are explained here -> [[TEUlt_file_fxs]] (this is a work in progress)
- source code changes: 
	- changes to integrate LTR Retriever -> [[LTRRet_integration]]
	- other random changes -> [[other_source_changes]]

!!! note 
	the entire edited source code is available on the github link in the top right

## Diagram
``` mermaid 
graph TD
	F(1. TEUlt setup) --> A;
	F(1. TEUlt setup) --> B;
	A(2.1. TEUlt annotations) -->C(Transposon Annotation);
	B(2.2. Manual Annotations) -->C(Transposon Annotation);
	C --> D(3. Combine Annotations);
	D --> E(4. Parse Annotations);
	E --> G(5. Run TEUlt Pipeline);
	G --> H(6. Annotation Stats);
	G --> I(7. Size Filtering);
	I --> J(8. Visualize);

```



## Individual steps
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

## Approximate runtimes 

| step | time | computer |
| ---- | ---- |---- |
| 2.1 (TEUlt annotations) | ~27 hours | Talapas |
| 2.2 (manual annotations) | [[a2_2_anno_manual#Approximate runtimes]] | Talapas |
| 4 (parse annotations) | <1 min | Talapas |
| 5 (TEUlt pipeline) | ~100 min | Talapas |


