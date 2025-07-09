# DiaryBiome

<div align="center">
  <img src="DiaryBiome.png" alt="DiaryBiome Logo" width="200"/>
</div>

## Overview

DiaryBiome consists of two main components, each addressing a specific task in the metagenomic analysis workflow (task 1):

### Task 1: Bioinformatics data processing (`DiaryBiome_Preprocess/`)
A reproducible, efficient, and easy-to-share bioinformatics workflow covering essential preprocessing and taxonomic classification of metagenomic data.

### Task 2: Statistical Analysis (`DiaryBiome_Analysis/`)
Comprehensive diversity analyses and differential abundance analysis between dietary supplement and yogurt samples using the processed data from processing step.

## Project Structure

```
DiaryBiome/
├── DiaryBiome_Preprocess/     # Task 1: Bioinformatics Data Processing
│   ├── config/                # Pipeline configuration
│   ├── envs/                  # Conda environments
│   ├── data/                  # Input data and samples
│   ├── results/               # Processing outputs
│   ├── demo_output/           # Example results
│   └── Snakefile              # Snakemake workflow
├── DiaryBiome_Analysis/       # Task 2: Statistical Analysis
│   └── [Analysis scripts and outputs]
├── DiaryBiome.png             # Project logo
└── README.md                  # This file
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