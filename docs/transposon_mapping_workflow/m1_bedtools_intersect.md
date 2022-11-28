# step 1 of [[m0_overall_mapping_workflow|overall mapping workflow]]

- use bedtools intersect function to determine overlap of genome 1 (N2) transposons with genome 2 (CB) SNPS relative to genome 1 (N2)
- this allows for generation of unique transposon sequences that can be tracked between genomes

## input and output files
<table cellpadding="5" style="border: 1px solid black">
    <tr style="border: 1px solid black">
        <td style="border: 1px solid black" >INPUT</td>
        <td style="border: 1px solid black">transposons.gff3 (the finaloutput from size filtered transposon ultimate data), snps vcf file</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">OUTPUT</td>
        <td style="border: 1px solid black">nasty text file with overlap between transposons sequences and SNPS (transposon sequence line listed on new line with every snp that it overlaps with)</td>
    </tr>
</table>
- run in command line


## bedtools command
```bash
bedtools intersect -wa -wb -a /FinalAnnotations_Transposons.gff3 -b SNPS.vcf
```

option | file input | genome
--- | --- | ---
-a | FinalAnnotations_Transposons.gff3 | 1
-b | SNPS.vcf | in genome 2 relative to genome 1

