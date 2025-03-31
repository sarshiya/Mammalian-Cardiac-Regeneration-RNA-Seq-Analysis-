## Transcriptional Profile of Mammalian Cardiac Regeneration with mRNA-Seq Project

This repository documents a complete RNA-seq analysis workflow, developed over several weeks as part of a course project. It reflects a full end-to-end pipeline — from raw FASTQ files to statistical inference and biological interpretation. The project is structured using Snakemake for workflow management and R (with various Bioconductor packages) for statistical and enrichment analysis.

---

##  Project Objective

The objective of this project was to apply RNA-seq analysis methods to a real-world dataset, replicate findings from a published paper, and interpret biological significance through differential expression and gene set enrichment.

This analysis is based on the dataset from the study:

> **O’Meara et al.**  
> *Transcriptional Reversion of Cardiac Myocyte Fate During Mammalian Cardiac Regeneration.*  
> Circ Res. Feb 2015. PMID: [25477501](https://pubmed.ncbi.nlm.nih.gov/25477501)

While this project captures the core biological signals observed in the original work, we intentionally deviate from the authors' exact methodology to apply more modern tools and workflows. This includes use of **Snakemake**, **DESeq2**, and **clusterProfiler**, offering a reproducible and scalable framework for RNA-seq analysis.

---

## Repository Structure

```
RNAseq-Project/
│
├── RNAseq-analysis-file.snake               # Snakemake pipeline (Week 1–3 merged)
├── differential_expression_analysis.Rmd     # Differential gene expression (DESeq2)
├── gene_set_enrichment_analysis.Rmd         # GO/KEGG enrichment analysis (GSEA)
├── discussion_questions.Rmd                 # Weekly conceptual responses
├── project_1_rnaseq.Rmd                     # Final report and synthesis
├── full_data_multiqc_report.html            # QC summary (FastQC + MultiQC)
├── Rhistory.txt                             # R console history & visuals used
├── README.md                                # You’re reading it now
```

---

## Pipeline Overview

The pipeline follows best practices for RNA-seq and includes the following major stages:

1. **Preprocessing**  
   - Quality control using **FastQC**
   - Trimming with **Trimmomatic**

2. **Alignment & Quantification**  
   - Read mapping using **HISAT2**
   - Counting reads with **featureCounts**

3. **Quality Assessment**  
   - Report aggregation using **MultiQC**

4. **Statistical Analysis**  
   - Differential expression analysis using **DESeq2**

5. **Pathway & Gene Set Enrichment**  
   - GO and KEGG enrichment using **clusterProfiler** and **enrichplot**

---

## Analysis Journey: A Walkthrough of the RMarkdown Files

This section walks through each `.Rmd` file from the perspective of an analyst performing the work.

### `RNAseq-analysis-file.snake`  
This file is the engine of the analysis — a streamlined and modular Snakemake pipeline that merges the logic and steps from Weeks 1 to 3. It handles quality trimming, alignment to the reference genome, generation of BAM files, and read quantification. It was designed for flexibility and reproducibility, with wildcard rules and proper input/output handling.

---

### `differential_expression_analysis.Rmd`  
After quantification, I transitioned into statistical analysis. Using **DESeq2**, I filtered low-count genes, normalized read counts, and constructed the design formula for differential analysis. From there, I generated visualizations like:

- Principal Component Analysis (PCA) plots
- MA plots
- Volcano plots for significant genes
- Heatmaps for clustering samples

This analysis revealed key upregulated and downregulated genes that aligned with the findings of the original paper.

---

### `gene_set_enrichment_analysis.Rmd`  
To move from gene-level to pathway-level insights, I conducted Gene Set Enrichment Analysis (GSEA). I:

- Annotated gene IDs using `org.Hs.eg.db`
- Ran GO (Biological Process, Cellular Component, Molecular Function) enrichment
- Ran KEGG pathway analysis
- Created enrichment visualizations:
  - Dot plots
  - Enrichment maps
  - Ridge plots for expression variation

This step helped frame the DEGs in biological pathways — such as immune response, apoptosis, or cell signaling — bringing life to raw expression shifts.

---

### `project_1_rnaseq.Rmd`  
This document is the polished synthesis of the full project. It walks through:

- Study context and dataset origin
- Snakemake workflow diagram (`my_workflow_updated.PNG`)
- Data characteristics
- Preprocessing and QC steps
- DE analysis with interpretation
- Enrichment and final biological conclusions

It reads like a scientific report and serves as the main deliverable.

---

### `discussion_questions.Rmd`  
This file contains weekly reflections and conceptual questions. It includes responses on topics like:

- Tool choice rationale (why HISAT2 over STAR)
- Limitations of DEG analysis
- Importance of multi-sample replicates
- Snakemake vs Bash scripting

Writing these helped me articulate and reflect on the analytical decisions throughout the project.

---

### `Rhistory.txt`  
A log of R commands and visual outputs generated during the analysis. It includes image references such as:

- `fastqc_plot.png`
- `gsea_plot.png`
- `my_workflow.PNG` and `my_workflow_updated.PNG`

These were integrated into the `.Rmd` files to support interpretation and storytelling.

---

## Visual Summary

The analysis produced key visuals such as:

- PCA and clustering heatmaps to assess sample variance
- Volcano plots highlighting significant DEGs
- GO/KEGG dot plots for enriched terms
- Workflow diagrams explaining the pipeline

All plots were created using `ggplot2`, `pheatmap`, `enrichplot`, and are embedded in the `.Rmd` reports.

---

## Tools & Dependencies

### Snakemake Tools
- `snakemake`
- `fastqc`, `trimmomatic`
- `hisat2`, `samtools`, `subread (featureCounts)`
- `multiqc`

### R Packages
- `DESeq2`, `tximport`
- `clusterProfiler`, `org.Hs.eg.db`
- `enrichplot`, `ggplot2`, `pheatmap`

---

## Reproducing the Analysis

After installing dependencies, run:

```bash
snakemake --cores 4
```

Then open `project_1_rnaseq.Rmd` in RStudio to render the final results to HTML or PDF.

---

##  Acknowledgements

This project is based on the dataset published in:

> **O’Meara et al.**  
> *Transcriptional Reversion of Cardiac Myocyte Fate During Mammalian Cardiac Regeneration.*  
> Circ Res. Feb 2015. PMID: [25477501](https://pubmed.ncbi.nlm.nih.gov/25477501)

We intentionally diverge from their original methods in favor of updated tools and practices while ensuring the core biological signals are faithfully captured and interpreted.

---

## Contact

If you're looking to reproduce this project, extend the workflow, or collaborate on a similar analysis — feel free to connect or open an issue. I'm happy to discuss improvements, additions, or adaptations of this pipeline for other datasets.
```


