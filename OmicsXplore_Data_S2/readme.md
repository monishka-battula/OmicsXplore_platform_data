OmicsXplore Data S2
===================

Supporting Information for "OmicsXplore: a fully cloud-based platform for
automated, end-to-end bioinformatics analysis, applied to RNA sequencing of
idiopathic pulmonary fibrosis lung tissue".

This archive holds the files exported by the OmicsXplore platform for the case
study of GSE92592 (BioProject PRJNA358081, SRA study SRP095361): 39 lung
tissue samples, 20 from patients with idiopathic pulmonary fibrosis (IPF,
SRR5120902 to SRR5120921) and 19 from control donors (SRR5120922 to
SRR5120940). Files are given as exported, except where noted below.


01_quality_control
------------------
multiqc_report_pretrim_qc.html
    MultiQC 1.35 report of the Pre-trim QC module (FastQC 0.12.1 on the 78 raw
    FASTQ files).
multiqc_report_posttrim_qc.html
    MultiQC 1.35 report of the Post-trim QC module (FastQC 0.12.1 on the 78
    trimmed paired FASTQ files).
multiqc_report_full_pipeline.html
    MultiQC report that aggregates the Trimmomatic, STAR and SAMtools logs of
    the whole run. It is the source of the trimming and alignment values in
    Tables S3a and S3c. Its FastQC section was built from the raw reads, so
    multiqc_report_posttrim_qc.html should be used for the trimmed reads. Its
    HTSeq-count section was generated before the final quantification and does
    not match the count matrix. Use
    02_alignment_and_quantification/count_matrix_statistics.json for the
    quantification statistics.

02_alignment_and_quantification
-------------------------------
samtools-flagstat-table.csv
    SAMtools 1.22.1 flagstat summary of the duplicate-marked BAM files
    (values in millions of alignments).
count_matrix_statistics.json
    HTSeq-count 2.0.5 statistics per sample (assigned, no_feature, ambiguous,
    alignment_not_unique, too_low_aQual and not_aligned pairs, features with
    counts and assignment rate). One trailing comma in the exported file was
    removed so that the file parses as standard JSON. No value was changed.
annotated_counts_IPF.csv
    Merged count matrix after the Annotation module (features by samples),
    with the identifiers assigned by g:Profiler g:Convert.

03_sample_metadata
------------------
IPF_meta_data.csv           Sample to group table used by the DEG analysis module.
SraRunTable_IPF_table1.csv  SRA run table of the 39 runs.
SRR_Acc_List_IPF_data.txt   Accession list entered into the Upload module.

04_differential_expression
--------------------------
Outputs of the DEG analysis module (PyDESeq2 0.5.4, GSEApy 1.3.1 with Enrichr).
Log2 fold changes, Wald statistics and normalised enrichment scores are
expressed as control relative to IPF (control as the numerator), as in the
article and in Data S1. Down-regulated features, with a negative
log2FoldChange, are therefore raised in IPF.
deseq2_full_results.csv      All 10,484 tested features (baseMean of 10 or more).
DEGs_filtered.csv            The 3,464 differentially expressed features
                             (adjusted P below 0.05, absolute log2 fold change
                             above 0.5).
DEGs_upregulated.csv         The 1,714 up-regulated features (positive log2
                             fold change), which are reduced in IPF.
DEGs_downregulated.csv       The 1,750 down-regulated features (negative log2
                             fold change), which are raised in IPF.
AllGenes_positiveLFC.csv     All tested features with a positive log2 fold change.
AllGenes_negativeLFC.csv     All tested features with a negative log2 fold change.
enrichment_results.csv       Enrichr over-representation analysis of the 100 most
                             significant genes against GO_Biological_Process_2023.
gsea_results.csv             Preranked GSEA against GO_Biological_Process_2023
                             (100 permutations).
pca_plot.png, volcano_plot.png, ma_plot.png, clustermap.png,
ora_barplot.png, ora_bubbleplot.png
                             Plots shown in Figures 3 and 4 of the article.
                             In these plots the IPF samples are labelled
                             Treatment.

05_alternative_splicing
-----------------------
splicekit_report_IPF.html
    Self-contained report of the Gene Splicing module (splicekit 0.8.1 with
    edgeR), contrast IPF versus control. Fold changes in this report are IPF
    relative to control, the opposite orientation to the DEG analysis module.

06_gene_fusions
---------------
SRR51209xx_fusions.pdf
    Arriba 2.5.0 visualisations of the candidate fusion events, one PDF per
    sample and one page per event (271 events in 38 files). SRR5120922 had no
    retained event and therefore has no file.

Licences and references for every engine are listed in Table S1 of the
Supporting Information.

