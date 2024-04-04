# Bacterial regulons in *Escherichia coli* with ChIP-seq and RNA-seq

## Publication

Myers KS, Park DM, Beauchene NA, Kiley PJ. Defining bacterial regulons using
ChIP-seq. Methods. 2015 Sep 15;86:80-8. doi: 10.1016/j.ymeth.2015.05.022. Epub
2015 May 29. Review. PubMed PMID: 26032817; PubMed Central PMCID: PMC4577457.

- PubMed PMID: [26032817](https://www.ncbi.nlm.nih.gov/pubmed/26032817)
- PubMed Central PMCID: [PMC4577457](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4577457/)


## Data availability

### Raw reads

GEO series [GSE41195](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE41195)

    **Subsets:**

    - [GSE41186](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE41186): Chip-chip from Escherichia coli MG1655 K-12, WT and ∆fnr strains
    
    - [GSE41187](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE41187)	Genome-wide analysis of FNR and σ70 in E. coli under aerobic and anaerobic growth conditions.
    
    - [GSE41189](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE41189)	Expression analysis of Escherichia coli MG1655 K-12 WT and ∆fnr mutant


### Reference genome

We download the reference genome from EnsemblGenomes Bacteria, release 37, strain and assembly identifier *Escherichia_coli_str_k_12_substr_mg1655.ASM584v2*.

- [Genome sequence (fasta format)](ftp://ftp.ensemblgenomes.org/pub/bacteria/release-37/fasta/bacteria_0_collection/escherichia_coli_str_k_12_substr_mg1655/dna/Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.dna.chromosome.Chromosome.fa.gz)
- [Genome annotations (GFF3 format)](ftp://ftp.ensemblgenomes.org/pub/bacteria/release-37/gff3/bacteria_0_collection/escherichia_coli_str_k_12_substr_mg1655/Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.chromosome.Chromosome.gff3.gz)
- [Genome annotations (GTF format)](ftp://ftp.ensemblgenomes.org/pub/release-37/bacteria/gtf/bacteria_0_collection/escherichia_coli_str_k_12_substr_mg1655/Escherichia_coli_str_k_12_substr_mg1655.ASM584v2.37.gtf.gz)


### Preprocessed dataset

We prepared a few small datasets that can be used for some courses for quick tests.


#### ChIP-seq

- Genome coverage files ([wig fixed step](https://genome.ucsc.edu/goldenPath/help/wiggle.html) format)

    - [FNR_200bp.wig](data/ChIP-seq/FNR_200bp.wig)
    - [input_200bp.wig](data/ChIP-seq/input_200bp.wig)
- Peaks returned by MACS2 and Homer peak-callers, resp. ([bed](https://genome.ucsc.edu/FAQ/FAQformat.html#format1) format)

    - [FNR1_vs_input1_cutadapt_bowtie2_homer.bed](data/ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_homer.bed)
    - [FNR1_vs_input1_cutadapt_bowtie2_macs2.bed](data/ChIP-seq/FNR1_vs_input1_cutadapt_bowtie2_macs2.bed)
    
#### RNA-seq


- Counts per gene ([tab-separated value](https://en.wikipedia.org/wiki/Tab-separated_values) format)

    - [cutadapt_bwa_featureCounts_all.tsv](data/RNA-seq/cutadapt_bwa_featureCounts_all.tsv)
