# Project Identity

This document defines the professional identity for this portfolio-ready project.

---

## Display Title
**GO Enrichment Analyzer for Arabidopsis**

## Repo Slug (Suggested)
`go-enrichment-arabidopsis`

## Tagline
Statistical Gene Ontology enrichment analysis with Fisher's exact test and FDR correction

## GitHub Description
A Python tool for identifying overrepresented Gene Ontology terms in Arabidopsis thaliana protein sets using statistical enrichment analysis with multiple testing correction.

## Primary Stack
- Python 3.x
- Jupyter Notebook
- pandas, numpy, scipy, statsmodels
- GO annotation data (UniProt GOA)

## Topics/Keywords
- bioinformatics
- gene-ontology
- enrichment-analysis
- arabidopsis-thaliana
- statistical-analysis
- functional-annotation
- computational-biology
- jupyter-notebook
- fisher-exact-test
- multiple-testing-correction

## Problem & Approach

**What problem it solves:**
When analyzing gene expression or proteomic studies, researchers often end up with lists of genes/proteins of interest. Understanding what biological functions, processes, or cellular components are overrepresented in these lists is crucial for biological interpretation. This tool performs Gene Ontology (GO) enrichment analysis to identify statistically significant functional patterns.

**Approach:**
- Load protein sets and GO annotations from UniProt GOA database
- Clean annotations (remove NOT qualifiers, IEA evidence)
- Separate by GO aspect (Biological Process, Molecular Function, Cellular Component)
- Calculate enrichment using Fisher's exact test
- Apply FDR (False Discovery Rate) correction for multiple testing
- Fetch GO term descriptions from QuickGO API
- Present ranked results with statistical significance

## Inputs & Outputs

**Inputs:**
- Protein set file (TSV): List of Arabidopsis Uniprot IDs
- GO annotation file (TSV): Full GOA annotations for Arabidopsis thaliana
- GO term metadata (TSV): Descriptions and relationships (optional, can fetch via API)

**Outputs:**
- Enriched GO terms table with:
  - GO term ID and description
  - Counts in protein set vs background
  - p-values from Fisher's exact test
  - FDR-corrected q-values
  - Enrichment scores
- Biological interpretation of enriched functions

---
