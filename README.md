# GO Enrichment Analyzer for Arabidopsis

**Statistical Gene Ontology enrichment analysis with Fisher's exact test and FDR correction**

**Stack:** Python, Jupyter Notebook, pandas, scipy, statsmodels

## Overview

This project performs Gene Ontology (GO) enrichment analysis to identify overrepresented biological processes, molecular functions, and cellular components in Arabidopsis thaliana protein sets. It demonstrates functional annotation and statistical interpretation of genomic data using Fisher's exact test with multiple testing correction.

## Problem & Approach

**Problem:** When analyzing gene expression or proteomic studies, researchers often end up with lists of genes/proteins of interest. Understanding what biological functions, processes, or cellular components are overrepresented in these lists is crucial for biological interpretation.

**Approach:**
- Load protein sets and GO annotations from UniProt GOA database
- Clean annotations (remove NOT qualifiers, exclude IEA evidence)
- Separate by GO aspect (Biological Process, Molecular Function, Cellular Component)
- Calculate enrichment using Fisher's exact test (2×2 contingency tables)
- Apply FDR (False Discovery Rate) correction for multiple testing
- Fetch GO term descriptions from QuickGO API
- Present ranked results with statistical significance

## Tech Stack

- Python 3.x
- Jupyter Notebook
- pandas - data manipulation
- numpy - numerical operations
- scipy - Fisher's exact test
- statsmodels - FDR correction
- requests - QuickGO API queries

## Repository Structure

```
gene-ontology-enrichment-python/
├── code/
│   ├── go_enrichment.ipynb         # Main GO enrichment analysis
│   ├── clustering_analysis.ipynb   # CD-HIT sequence clustering
│   ├── ex2.tsv                     # Example protein set (118 IDs)
│   ├── goa_arabidopsis.tsv         # Full GOA annotations (~159k)
│   ├── quickgo_term_info.tsv       # GO term metadata
│   └── content/                    # Clustering outputs (FASTA, plots)
├── requirements.txt
├── .gitignore
└── README.md
```

## Setup / Installation

```bash
# Clone the repository
git clone https://github.com/Raminyazdani/gene-ontology-enrichment-python.git
cd gene-ontology-enrichment-python

# Install dependencies
pip install -r requirements.txt
```

## How to Run

### GO Enrichment Analysis (Main)

```bash
cd code
jupyter notebook go_enrichment.ipynb
```

Run all cells in sequence. The notebook will:
1. Load protein set and GO annotations
2. Perform enrichment analysis for each GO aspect
3. Calculate p-values and FDR-corrected q-values
4. Display enriched terms with descriptions

### Clustering Analysis

```bash
cd code
jupyter notebook clustering_analysis.ipynb
```

This notebook demonstrates CD-HIT protein sequence clustering at various identity thresholds.

**Note:** Both notebooks expect to be run from the `code/` directory due to relative paths for data files.

## Data / Inputs

**Included in repository:**
- `ex2.tsv` - Example Arabidopsis protein set (118 Uniprot IDs)
- `goa_arabidopsis.tsv` - Full GO annotations for A. thaliana from UniProt GOA
- `quickgo_term_info.tsv` - GO term descriptions and metadata

**Format:**
- Protein set: Single column TSV with Uniprot IDs (no header)
- GOA file: Columns: Uniprot, qualifier, go_term, aspect, evidence_code
- Term info: Columns: GO_term, name, aspect

**To use your own data:**
1. Prepare a protein set file with one Uniprot ID per line
2. Download GO annotations from [UniProt GOA](https://www.ebi.ac.uk/GOA/)
3. Update file paths in the notebook configuration cells

## Outputs

**GO Enrichment Results:**
- Enriched GO terms ranked by significance
- For each term:
  - GO ID and description
  - Count in protein set vs background
  - p-value from Fisher's exact test
  - FDR-corrected q-value
  - Enrichment score (log2 fold-change)
- Separate results for Biological Process, Molecular Function, Cellular Component

**Example Output:**
```
GO:0006950  response to stress  
  - Protein set: 25/118 (21.2%)
  - Background: 2500/27000 (9.3%)
  - p-value: 1.2e-5
  - q-value: 0.0008
  - Enrichment: 1.19
```

## Reproducibility Notes

- Python 3.x recommended (tested on 3.8+)
- All dependencies specified in requirements.txt
- Random seed not applicable (deterministic statistical tests)
- GO annotations version: included snapshot from Dec 2025
- For updated annotations, download from UniProt GOA

## Troubleshooting

**Issue:** `FileNotFoundError` when running notebooks
- **Solution:** Ensure you run notebooks from the `code/` directory: `cd code && jupyter notebook`

**Issue:** Import errors for scipy/statsmodels
- **Solution:** Install requirements: `pip install -r requirements.txt`

**Issue:** QuickGO API requests fail
- **Solution:** Check internet connection; GO term IDs will still be shown, just without descriptions

**Issue:** Large memory usage with full GOA file
- **Solution:** GOA file is ~6MB and ~159k rows; should work on systems with 4GB+ RAM

## References

- UniProt GOA: https://www.ebi.ac.uk/GOA/
- Gene Ontology: http://geneontology.org/
- QuickGO API: https://www.ebi.ac.uk/QuickGO/

