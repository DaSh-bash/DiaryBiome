# DiaryBiome_Preprocess

<div align="center">
  <img src="../DiaryBiome.png" alt="DiaryBiome Logo" width="200"/>
</div>

## Overview

DiaryBiome is a lightweight Snakemake pipeline designed for bioinformatic preprocessing of yogurt and dietary supplement metagenomic samples. This pipeline corresponds to the workflow component of Task 1.

DiaryBiome requires minimal installation and compactly performs analysis of a given dataset of yogurt and dietary supplement human metagenome data.

The pipeline uses the KneadData suite to simultaneously handle read quality control (such as sequence length distribution and quality), remove low-quality reads, trim adapters (via Trimmomatic), and remove human sequencing reads (using Bowtie2).

Kraken2 + Bracken are used for taxonomic classification and abundance estimates, chosen for their efficiency and ease of use. Kraken2 is one of the most time- and memory-efficient algorithms available.

Finally, the pipeline produces a BIOM-like table with combined output results and a comprehensive quality control report of all performed steps (using MultiQC).

## Quick start

### Prerequisites
- [Snakemake](https://snakemake.readthedocs.io/) (≥7.0)
- [Conda](https://docs.conda.io/)
- Python ≥3.8

### Databases / config
DiaryBiome requires a human genome for mapping contaminated reads ([KneadData database setup](https://huttenhower.sph.harvard.edu/kneaddata/)) and a database for Kraken2 and Bracken ([Kraken2 database setup](https://ccb.jhu.edu/software/kraken2/index.shtml?t=manual)). These should be provided in the data directory and the path indicated in `config/config.yml`.

### Pipeline installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd DiaryBiome/DiaryBiome_Preprocess
   ```

2. **Set up the conda environment:**
   ```bash
   conda env create -f envs/environment.yml
   conda activate metagenome
   ```

3. **Configure the pipeline:**
   - Edit `config/config.yml` for your specific parameters
   - Update `data/samples.txt` with your sample IDs

### Running the pipeline

1. **Navigate to the pipeline directory:**
   ```bash
   cd DiaryBiome/DiaryBiome_Preprocess
   ```
2. **Run the preprocessing pipeline:**
   ```bash
   snakemake --cores 8 --use-conda
   ```

## Directory structure

```
DiaryBiome_Preprocess/
├── config/              # Configuration files
│   └── config.yml       # Pipeline parameters
├── envs/                # Conda environment files
│   └── environment.yml  # Main environment
├── data/                # Input data directory
│   └── samples.txt      # Sample IDs
├── results/             # Output directory
├── demo_output/         # Example outputs
├── Snakefile            # Main workflow file
├── README.md            # Pipeline documentation
└── .gitignore           # Git ignore rules
```

## Workflow steps

### Detailed processing pipeline

1. **Data download (`download_fastq`):**
   - Downloads paired-end FASTQ files from SRA using `fasterq-dump`
   - Output: `data/{sample}_1.fastq`, `data/{sample}_2.fastq`

2. **Quality control & host removal (`kneaddata`):**
   - Performs FastQC analysis on raw reads
   - Trims adapters using Trimmomatic with parameters: `SLIDINGWINDOW:4:20 MINLEN:50`
   - Removes human genome sequences using Bowtie2 with `--very-fast` mode
   - Output: `results/kneaddata/{sample}_kneaddata_paired_1.fastq`, `results/kneaddata/{sample}_kneaddata_paired_2.fastq`

3. **Taxonomic classification (`kraken2`):**
   - Classifies reads using Kraken2 with 8 threads
   - Output: `results/kraken2/{sample}.kraken2_report.txt`, `results/kraken2/{sample}.kraken2`

4. **Abundance estimation (`bracken`):**
   - Estimates species-level abundance using Bracken with 10 threads
   - Parameters: read length 100, species level (-l S)
   - Output: `results/bracken/{sample}.bracken`, `results/bracken/{sample}.breport`

5. **Quality control report (`multiqc`):**
   - Generates comprehensive QC report combining all analysis steps
   - Output: `results/multiqc_report/multiqc_report.html`

6. **Abundance table generation (`bracken_to_abundance_table`):**
   - Combines all Bracken outputs into a single BIOM-like table
   - Output: `results/combined_abundance_table.tsv`

## Output files

### Preprocessing outputs
- **Quality reports:** `results/kneaddata/fastqc/` - FastQC quality reports before and after processing
- **Cleaned reads:** `results/kneaddata/` - Quality-filtered and host-removed reads
- **Taxonomic classification:** `results/kraken2/` - Kraken2 classification results and reports
- **Abundance tables:** `results/bracken/` - Bracken abundance estimates and reports
- **Combined abundance table:** `results/combined_abundance_table.tsv` - Merged abundance data
- **MultiQC report:** `results/multiqc_report/multiqc_report.html` - Comprehensive QC summary

## Contact
For questions and support:
- **Email:** daria.shipilina@gmail.com
