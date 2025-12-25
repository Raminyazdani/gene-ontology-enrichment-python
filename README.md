# Gene Ontology Enrichment Analysis

**GO term analysis and functional annotation of biological data**

**Stack:** Python, Jupyter Notebook

## Overview

This project performs Gene Ontology (GO) enrichment analysis to identify overrepresented biological processes, molecular functions, and cellular components in gene sets. It demonstrates functional annotation and interpretation of genomic data.

## Problem & Approach

**Problem:** Identify enriched biological functions in gene lists through GO term analysis.

**Approach:**
- Load and parse GO annotation files
- Perform enrichment analysis
- Calculate statistical significance (p-values, FDR)
- Visualize enriched terms
- Interpret biological meaning

## Tech Stack

- Python 3.x
- Jupyter Notebook
- Pandas for data manipulation
- Statistical libraries for enrichment

## Folder Structure

```
pobd4/
├── code/
│   ├── assignment_4_1.ipynb    # GO analysis part 1
│   └── assignment_4_2.ipynb    # GO analysis part 2
├── data/
│   └── *.tsv                   # GO annotation files
├── requirements.txt
└── README.md
```

## Setup / Installation

```bash
pip install -r requirements.txt
```

## How to Run

```bash
cd pobd4/code
jupyter notebook
```

## Data / Inputs

- GO annotation TSV files
- Gene lists for enrichment analysis

## Outputs

- Enriched GO terms with p-values
- Functional annotation results
- Visualization of enrichment

## Reproducibility Notes

- Relative paths to data files
- Originally created in an academic setting

## Notes

- Two notebooks covering different GO analysis aspects
- GO annotation files included
- Statistical enrichment methods implemented
