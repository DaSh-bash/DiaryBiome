# Downstream analysis workflow

This repository contains a downstream analysis workflow for metagenomic data on yogurt and dietary supplement samples using DESeq2. It corresponds to task 2.

Before continuing with downstream analysis quality of preprocessing needs to be evaluated: 

**📊 MultiQC Report**: [View the complete MultiQC quality assessment report](../DiaryBiome_Preprocess/demo_output/results/multiqc_report/multiqc_report.html)

## Files

- `DiaryBiome_Analysis.Rmd` - Main analysis workflow (R Markdown)
- `config.yaml` - Configuration file with all analysis parameters
- `environment.yml` - Conda environment for reproducible dependencies
- `SraRunTable.csv` - SRA metadata file
- `README.md` - This documentation file

## Setup Instructions
1. **Create the conda environment**:
   ```bash
   conda env create -f environment.yml
   ```
2. **Activate the environment**:
   ```bash
   conda activate diarybiome_analysis
   ```

## Running the Analysis
```bash
conda activate diarybiome_analysis

# Run the main analysis
Rscript -e "rmarkdown::render('DiaryBiome_Analysis.Rmd', output_format = 'html_document')"

## Output Files
The workflow generates the following output files:
- `DiaryBiome_Analysis.html` - Complete analysis report
