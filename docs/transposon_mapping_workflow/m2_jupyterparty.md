# step 2 of [overall mapping workflow](m0_overall_mapping_workflow.md)
!!! info "previous step:"
    [m1_bedtools_intersect](m1_bedtools_intersect.md)

- after running bedtools intersect to get overlap between TEs and SNPs, can then plug in all files to jupyter notebook

jupyter notebook: [[TEUlt_find_unique_TEs_7.ipynb]]


file | chromosome names
--- | ---
SNP vcf | N2_chrI, N2_chrII... (converted to Chr I, Chr II... when imported)
bedtools intersect txt | seq1, seq2... (converted to Chr I, Chr II... when imported)
chrom lengths txt | I, II... (converted to Chr I, Chr II... using fx fix_chr_names)
size filtered TE gff3 | seq1, seq2... (converted to Chr I, Chr II... when imported)



variable to define | filepath to...
--- | ---
intersect_file | text file output from bedtools intersect
libN2_fasta | sequence of N2 in fasta format
libCB_fasta | sequence of CB in fasta format
vcf_file | SNPs vcf
N2_file | size filtered N2 TE gff3
CB_file | size filtered CB TE gff3
chr_lengths_file | text file with lengths of all 6 chromosomes for both genomes

this jupyter notebook will spit out files to make the RIdeogram in the next step in R