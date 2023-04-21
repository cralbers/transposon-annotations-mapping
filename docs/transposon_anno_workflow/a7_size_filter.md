---
aliases: [step 7]
---
# Step 7 of [overall annotation workflow](a0_overall_anno_workflow.md)
!!! info "previous step:"
    [a6_anno_stats](a6_anno_stats.md)

- now need to implement manual size filtering step to get rid of TEs that are outside of canonical literature ranges because programs in TEUlt will sometimes annotate HUGE portions of chromosomes as TEs
- python function (in .py file and jupyter notebook)
	- [[TEUlt_reasonaTE_sizefilter.py]] (python file)
	- [[TEUlt_reasonaTE_sizefilter.ipynb]] (jupyter notebook)
- this is really tricky because how do you establish parameters that do not eliminate tandem repeats or nested TEs, but also get rid of ridiculous TEs?
	- scan for tandem repeats with another program and compare to TEs eliminated using stringent parameters?
    - use Tandem Repeat Finder to find tandem repeats and their overlap with annotated TEs? [TRF paper](https://academic.oup.com/nar/article/27/2/573/1061099?login=true)
    - use Red to detect de novo repeats and their overlap with annotated TEs? [Red paper](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-015-0654-5)


## In & out:
<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">gff3 output files from TEUlt, txt file of chromosome lengths</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">new gff3 with only TEs that made it through size filtering</td>
    </tr>
</table>

## Size parameters
Two sets of size parameters- stringent and non-stringent. I decided on these based on the spreadsheet attached below, which outlines the transposon classes annotated by these programs and current research on their characteristics, including their canonical sizes.
[[transposons.xlsx]]

### Stringent size parameters
- DNA:

TE | size (bp) 
------------ | ------------
Helitron | 4500
CMC | 2500
Zator | 1800-2400
hAT | 1000-2000
Sola | 1- 2000-6000, 2- 4000-5000, 3- 5000-7000
Tc1/Mariner | 1600
MITE | 100-800
Novosib | 

- Retro:

TE | size (bp) 
------------ | ------------
Gypsy | 9000
Copia| 5000
LINEs| 5000
SINEs| 600
ERV| 8000


### Non-stringent size parameters
- DNA:

TE | size (bp) 
------------ | ------------
Helitron | 20000
CMC | 20000
Zator | 15000
hAT | 20000
Sola | 7000
Tc1/Mariner | 20000
MITE | 1000
Novosib | 3000

- Retro:

TE | size (bp) 
------------ | ------------
Gypsy | 20000
Copia| 20000
LINEs| 10000
SINEs| 600
ERV| 8000


