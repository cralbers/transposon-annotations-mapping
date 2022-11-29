---
aliases: [overall annotation workflow]
---
# ANNOTATIONS
---
these notes are located at https://cralbers.github.io/transposon-annotations-mapping/

## table of contents
major steps of the transposon annotation and tracking workflow i used because my file organization is absolutely horrific and I want to learn how to use this obsidian program and also apparently i am accountable for what i did lol.

- all of the individual functions that are defined within the TEUlt are explained here -> [[TEUlt_file_fxs]]
- changes to integrate LTR Retriever -> [[LTRRet_integration]]
- other random changes to source code -> [[other_source_changes]]


``` mermaid 
graph TD
	F[[a1_TEUlt_setup]] --> A
	F[[a1_TEUlt_setup]] --> B
	A[[a2_1_anno_TEUlt]] -->C(Transposon Annotation)
	B[[a2_2_anno_manual]] -->C(Transposon Annotation)
	C --> D[[a3_anno_combine]]
	D --> E[[a4_anno_parse]]
	E --> G[[a5_anno_pipeline]]
	G --> H[[a6_anno_stats]]
	G --> I[[a7_size_filter]]
	I --> J[[a8_make_pictures]]


class A,B,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z internal-link;

```
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
