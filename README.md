# DiaryBiome

<div align="center">
  <img src="DiaryBiome.png" alt="DiaryBiome Logo" width="200"/>
</div>

## Overview

DiaryBiome consists of two main components, each addressing a specific task in the metagenomic analysis workflow (task 1):

### Task 1: Bioinformatics data processing (`DiaryBiome_Preprocess/`)
A reproducible, efficient, and easy-to-share bioinformatics workflow covering essential preprocessing and taxonomic classification of metagenomic data.

### Task 2: Statistical analysis (`DiaryBiome_Analysis/`)
Comprehensive diversity and differential abundance analysis between dietary supplement and yogurt samples using the processed data from processing step.

## Project structure

```
DiaryBiome/
├── DiaryBiome_Preprocess/         # Bioinformatics Data Processing
│   ├── config/                    # Pipeline configuration
│   │   └── config.yml
│   ├── envs/                      # Conda environments
│   │   └── environment.yml
│   ├── data/                      # Input data and samples
│   │   └── samples.txt
│   ├── results/                   # Processing outputs (empty by default)
│   ├── demo_output/               # Example results
│   │   └── results/
│   │       ├── bracken/
│   │       │   ├── SRR11605259.bracken
│   │       │   └── SRR11605259.breport
│   │       ├── combined_abundance_table.tsv
│   │       ├── kneaddata/
│   │       ├── kraken2/
│   │       └── multiqc_report/
│   │           ├── multiqc_data/
│   │           └── multiqc_report.html
│   ├── Snakefile                  # Snakemake workflow
│   └── README.md                  # Pipeline documentation
├── DiaryBiome_Analysis/           # Statistical Analysis
│   ├── DiaryBiome_Analysis.Rmd    # Main analysis workflow (R Markdown)
│   ├── DiaryBiome_Analysis.html   # Rendered analysis report
│   ├── config.yaml                # Analysis configuration
│   ├── environment.yml            # Conda environment for analysis
│   ├── SraRunTable.csv            # SRA metadata
│   └── README.md                  # Analysis documentation
├── DiaryBiome.png                 # Project logo
├── .gitignore                     # Git ignore rules
└── README.md                      # This file
```

## Quick Start

### Prerequisites
- [Snakemake](https://snakemake.readthedocs.io/) (≥7.0)
- [Conda](https://docs.conda.io/)
- Python ≥3.8
- R ≥4.0 (for statistical analysis)

### Installation
Installation and running instructions can be found in corresponding folders


## Contact
For questions and support:
- **Email:** daria.shipilina@gmail.com