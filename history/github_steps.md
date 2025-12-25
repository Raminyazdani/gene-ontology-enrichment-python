# Git History Reconstruction: GO Enrichment Analyzer for Arabidopsis

This document describes the realistic step-by-step development history for this repository, from initial project setup to the final portfolio-ready state.

---

## Development Narrative

This project evolved from an initial idea to perform Gene Ontology enrichment analysis on Arabidopsis protein sets. The development followed a typical research-oriented workflow with iterative improvements.

---

## Step-by-Step History

### Step 01: Initial Repository Setup
**Commit Message:** `Initial commit: Set up repository structure`

**Description:** Created the basic repository structure with README, .gitignore, and minimal documentation.

**Files Created:**
- README.md (basic project description)
- .gitignore (Python/Jupyter exclusions)
- LICENSE (if applicable)

**Rationale:** Standard repository initialization following best practices for Python projects.

---

### Step 02: Add Core Dependencies
**Commit Message:** `Add requirements.txt with core dependencies`

**Description:** Defined the Python package dependencies needed for data analysis and notebook execution.

**Files Created:**
- requirements.txt (pandas, jupyter, requests, scipy, statsmodels, numpy)

**Rationale:** Documenting dependencies early ensures reproducibility and makes it clear what libraries are needed.

---

### Step 03: Add Data Files
**Commit Message:** `Add GO annotation data and protein set`

**Description:** Added the input data files needed for enrichment analysis.

**Files Created:**
- code/ex2.tsv (118 Arabidopsis protein IDs)
- code/goa_arabidopsis.tsv (full GOA annotations, ~159k rows)
- code/quickgo_term_info.tsv (GO term metadata)

**Rationale:** Data is essential for the analysis. These files represent publicly available GO annotations from UniProt and a curated protein set for analysis.

---

### Step 04: Implement GO Enrichment Analysis
**Commit Message:** `Add GO enrichment analysis notebook`

**Description:** Created the main analysis notebook implementing statistical GO enrichment with Fisher's exact test.

**Files Created:**
- code/go_enrichment.ipynb

**Key Features:**
- Loads protein set and GOA annotations
- Filters annotations (removes NOT qualifiers, IEA evidence)
- Separates by GO aspect (P/F/C)
- Calculates enrichment using Fisher's exact test
- Applies FDR correction for multiple testing
- Fetches GO term descriptions from QuickGO API

**Rationale:** This is the core functionality of the project - identifying statistically significant GO term enrichment.

---

### Step 05: Add Sequence Clustering Analysis
**Commit Message:** `Add CD-HIT clustering analysis notebook`

**Description:** Created a companion notebook for protein sequence clustering analysis.

**Files Created:**
- code/clustering_analysis.ipynb
- code/content/ (directory for FASTA files and clustering outputs)

**Files in content/:**
- ex1.fasta (original sequences)
- ex1_cluster*.fasta (clustered sequences at various thresholds)
- ex1_cluster*.fasta.clstr (CD-HIT cluster files)
- ex1_cluster*_barplot.png (visualization of cluster distribution)

**Rationale:** Sequence clustering complements GO enrichment by helping identify redundant proteins before enrichment analysis.

---

### Step 06: Documentation Enhancement
**Commit Message:** `Enhance README with detailed usage instructions`

**Description:** Expanded README with comprehensive setup instructions, data descriptions, and troubleshooting.

**Files Modified:**
- README.md

**Improvements:**
- Added detailed problem statement and approach
- Documented tech stack comprehensively
- Included repository structure diagram
- Added setup and run instructions
- Documented data formats and sources
- Included example outputs
- Added troubleshooting section
- Listed references

**Rationale:** Professional documentation is essential for portfolio projects and helps users understand and run the code.

---

### Step 07: Add Project Metadata
**Commit Message:** `Add project identity and tracking documentation`

**Description:** Created metadata files for project identity and portfolio documentation.

**Files Created:**
- project_identity.md (professional project identity)
- report.md (transformation log)
- suggestion.txt (issue ledger)
- suggestions_done.txt (change ledger)

**Rationale:** These files document the project's professional framing and transformation process for portfolio readiness.

---

## Development Timeline (Conceptual)

If this were a real development process, the timeline might look like:

1. **Week 1:** Initial setup and data acquisition (Steps 01-03)
2. **Week 2-3:** Core GO enrichment implementation (Step 04)
3. **Week 3-4:** Clustering analysis addition (Step 05)
4. **Week 4:** Documentation and polish (Steps 06-07)

---

## Technical Decisions

### Why Fisher's Exact Test?
Fisher's exact test is the gold standard for GO enrichment analysis because:
- Handles small sample sizes well
- Provides exact p-values (no approximation)
- Widely used in bioinformatics literature
- Appropriate for 2×2 contingency tables (term present/absent × protein in set/background)

### Why FDR Correction?
Multiple testing correction is essential when testing hundreds or thousands of GO terms:
- Controls false discovery rate rather than family-wise error rate
- More statistical power than Bonferroni
- Standard practice in genomics and bioinformatics

### Path Design Decision
Used relative paths with clear working directory documentation:
- Simple and maintainable
- Works consistently when run from documented location
- Avoids complexity of dynamic path resolution
- Clearly documented in README and notebook comments

---

## Final State

The final repository (Step 07) represents a portfolio-ready project with:
- ✅ Professional naming (no academic terminology)
- ✅ Clean, well-documented code
- ✅ Comprehensive README
- ✅ Reproducible analysis (requirements.txt)
- ✅ Clear project identity
- ✅ Proper .gitignore
- ✅ Complete metadata documentation

---
