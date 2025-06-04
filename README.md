# AmpliconSeq_pipeline 

Amplicon-seq is a targeted sequencing method that enables high-throughput analysis of specific genomic regions, commonly used to assess genetic variation or DNA methylation at predefined loci. This repository provides a minimal, exemplar pipeline for processing bisulfite amplicon-seq FASTQ files (via shell script) and performing downstream methylation analysis (via R).

## Contents
- run_amplicon.sh — Bash script to process raw FASTQ files using trim_galore and bismark, producing .cov.gz methylation reports.
- ampliconseq_analysis.Rmd — R Markdown script for downstream QC and exploratory analysis (e.g., methylation distribution, PCA, gene-level plots).
- ampliconseq_analysis.html — Rendered HTML version of the R analysis.
- cpg_gene_plot.pdf — Example figure generated during the analysis.


## Requirements
	trim_galore
	bismark (with Bowtie2)
	samtools
	R with the following packages:
	- ggplot2, pheatmap, tidyverse, plotly, ggfortify, etc.

See the .Rmd file for package usage.

## Usage

1.	Preprocessing:

Run the following command to generate methylation coverage files (.cov.gz) using Bismark:
```
bash run_amplicon.sh sample.R1.fq.gz sample.R2.fq.gz /path/to/bismark_index &
```
This will produce .cov.gz files in the current directory and log detailed command execution in sample.log.

2.	Analysis in R:

Open or knit ampliconseq_analysis.Rmd in RStudio or via command line to generate the HTML report:

```
rmarkdown::render("ampliconseq_analysis.Rmd")
```

## Visualization
![Example plot](./cpg_gene_plot.png)

## License

MIT License