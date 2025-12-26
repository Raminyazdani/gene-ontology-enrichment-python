# Git History Reconstruction: GO Enrichment Analyzer for Arabidopsis

This document describes the realistic step-by-step development history for this repository, from initial project setup to the final portfolio-ready state.

---

## History Expansion Note

**Previous historian run:** 7 steps  
**Current historian run:** 11 steps  
**Expansion multiplier:** 1.57× (exceeds 1.5× requirement)

### Mapping from Old Steps to New Steps

This expansion creates a more granular, realistic development history by:
1. Splitting large commits into smaller, focused changes
2. Inserting realistic mistake → hotfix sequences
3. Maintaining identical final state

**Mapping:**
- Old step 01 (Initial setup) → **New steps 01-02** (split: README/LICENSE separate from .gitignore)
- Old step 02 (Add requirements) → **New step 03** (same)
- Old step 03 (Add data) → **New step 04** (same)
- Old step 04 (GO enrichment) → **New steps 05-07** (split: initial version with bug, hotfix, then FDR enhancement)
  - **Step 05:** OOPS - Wrong data path in notebook
  - **Step 06:** HOTFIX - Fix data path
  - **Step 07:** Enhancement - Add FDR correction
- Old step 05 (Clustering) → **New steps 08-09** (split: notebook separate from outputs)
- Old step 06 (Documentation) → **New step 10** (same)
- Old step 07 (Project metadata) → **New step 11** (same, final state)

### Deliberate Mistake → Hotfix Sequence (Steps 05-06)

**What broke (Step 05):**
In the initial implementation of `go_enrichment.ipynb`, the data file paths were incorrectly specified with an absolute path pattern that wouldn't work across different environments:
```python
protein_set_path = "/data/ex2.tsv"  # Wrong: absolute path
goa_path = "/data/goa_arabidopsis.tsv"  # Wrong: absolute path
```

**How it was noticed:**
When attempting to run the notebook from the `code/` directory (the intended working directory), the notebook failed with `FileNotFoundError` because the absolute paths didn't exist on the system.

**What fixed it (Step 06):**
Changed to relative paths that work when running from the `code/` directory:
```python
protein_set_path = "./ex2.tsv"  # Fixed: relative path from code/
goa_path = "./goa_arabidopsis.tsv"  # Fixed: relative path from code/
```

This is a realistic mistake that developers make when first creating a notebook - using absolute paths from their local environment that don't work for others. The immediate hotfix in the next commit is typical developer behavior.

---

## Development Narrative

This project evolved from an initial idea to perform Gene Ontology enrichment analysis on Arabidopsis protein sets. The development followed a typical research-oriented workflow with iterative improvements and a few course corrections along the way.

---

## Step-by-Step History

### Step 01: Initial Repository Setup
**Commit Message:** `Initial commit: Set up basic repository structure`

**Description:** Created the foundational repository files - README with basic project description and LICENSE.

**Files Created:**
- README.md (basic project overview)
- LICENSE (MIT license)

**Rationale:** Standard repository initialization. Starting with just the core documentation files before adding configuration.

---

### Step 02: Add Python .gitignore
**Commit Message:** `Add .gitignore for Python and Jupyter`

**Description:** Added .gitignore to exclude Python cache files, Jupyter checkpoints, and IDE files.

**Files Created:**
- .gitignore (Python, Jupyter, IDE exclusions)

**Rationale:** Added in separate commit after realizing Python-specific ignores were needed. This is typical - developers often add .gitignore after initial commit.

---

### Step 03: Add Core Dependencies
**Commit Message:** `Add requirements.txt with core dependencies`

**Description:** Defined the Python package dependencies needed for data analysis and notebook execution.

**Files Created:**
- requirements.txt (pandas, jupyter, requests, scipy, statsmodels, numpy)

**Rationale:** Documenting dependencies early ensures reproducibility and makes it clear what libraries are needed.

---

### Step 04: Add Data Files
**Commit Message:** `Add GO annotation data and protein set`

**Description:** Added the input data files needed for enrichment analysis.

**Files Created:**
- code/ (new directory)
- code/ex2.tsv (118 Arabidopsis protein IDs)
- code/goa_arabidopsis.tsv (full GOA annotations, ~159k rows)
- code/quickgo_term_info.tsv (GO term metadata)

**Rationale:** Data is essential for the analysis. These files represent publicly available GO annotations from UniProt and a curated protein set for analysis.

---

### Step 05: Implement GO Enrichment Analysis (Initial - With Bug)
**Commit Message:** `Add GO enrichment analysis notebook`

**Description:** Created the main analysis notebook implementing statistical GO enrichment with Fisher's exact test. **Note:** This version contained a path bug that was fixed in the next commit.

**Files Created:**
- code/go_enrichment.ipynb

**Key Features:**
- Loads protein set and GOA annotations
- Filters annotations (removes NOT qualifiers, IEA evidence)
- Separates by GO aspect (P/F/C)
- Calculates enrichment using Fisher's exact test
- Fetches GO term descriptions from QuickGO API

**Bug:** Used absolute paths `/data/ex2.tsv` and `/data/goa_arabidopsis.tsv` which didn't work.

**Rationale:** This represents the initial implementation of the core functionality.

---

### Step 06: Fix Data Paths in GO Enrichment Notebook
**Commit Message:** `Fix: Use relative paths for data files in go_enrichment.ipynb`

**Description:** Fixed the data loading paths to use relative paths that work when running from the `code/` directory.

**Files Modified:**
- code/go_enrichment.ipynb

**Changes:**
- Changed `/data/ex2.tsv` → `./ex2.tsv`
- Changed `/data/goa_arabidopsis.tsv` → `./goa_arabidopsis.tsv`
- Changed `/data/quickgo_term_info.tsv` → `./quickgo_term_info.tsv`

**Rationale:** Hotfix for the path issue discovered when trying to run the notebook. This is a realistic mistake - absolute paths from local environment that don't work elsewhere.

---

### Step 07: Add FDR Correction to GO Enrichment
**Commit Message:** `Enhance GO enrichment with FDR multiple testing correction`

**Description:** Enhanced the GO enrichment analysis by adding False Discovery Rate (FDR) correction for multiple testing.

**Files Modified:**
- code/go_enrichment.ipynb

**Enhancements:**
- Imported statsmodels for FDR correction
- Applied FDR correction to p-values using Benjamini-Hochberg method
- Added q-value column to results
- Updated result presentation to show both p-values and q-values

**Rationale:** Multiple testing correction is essential for GO enrichment analysis when testing hundreds of terms. This enhancement makes the statistical analysis more rigorous.

---

### Step 08: Add Sequence Clustering Analysis Notebook
**Commit Message:** `Add CD-HIT clustering analysis notebook`

**Description:** Created a companion notebook for protein sequence clustering analysis using CD-HIT.

**Files Created:**
- code/clustering_analysis.ipynb

**Key Features:**
- CD-HIT installation and setup
- Clustering at multiple identity thresholds (40%, 50%, 70%, 90%, 95%)
- Cluster distribution analysis

**Rationale:** Sequence clustering complements GO enrichment by helping identify redundant proteins before enrichment analysis.

---

### Step 09: Add Clustering Outputs and Visualizations
**Commit Message:** `Add CD-HIT clustering results and visualizations`

**Description:** Added the clustering output files and visualization plots generated by the clustering analysis.

**Files Created:**
- code/content/ (directory for outputs)
- code/content/ex1.fasta (original sequences)
- code/content/ex1_cluster*.fasta (clustered sequences at various thresholds - 5 files)
- code/content/ex1_cluster*.fasta.clstr (CD-HIT cluster files - 5 files)
- code/content/ex1_cluster*_barplot.png (cluster distribution plots - 5 files)

**Rationale:** Separating the outputs from the notebook commit keeps the version control more manageable. These are generated results that accompany the clustering analysis.

---

### Step 10: Documentation Enhancement
**Commit Message:** `Enhance README with detailed usage instructions and troubleshooting`

**Description:** Expanded README with comprehensive setup instructions, data descriptions, troubleshooting, and professional formatting.

**Files Modified:**
- README.md

**Improvements:**
- Added detailed problem statement and approach
- Documented tech stack comprehensively
- Included repository structure diagram
- Added setup and run instructions with working directory notes
- Documented data formats and sources
- Included example outputs
- Added troubleshooting section for common issues
- Listed references (UniProt GOA, QuickGO, Gene Ontology)

**Rationale:** Professional documentation is essential for portfolio projects. This makes the project accessible to others and demonstrates clear communication skills.

---

### Step 11: Add Project Metadata (Final Portfolio-Ready State)
**Commit Message:** `Add project identity and portfolio tracking documentation`

**Description:** Created metadata files for project identity and portfolio documentation, achieving final portfolio-ready state.

**Files Created:**
- project_identity.md (professional project identity document)
- report.md (transformation log and verification report)
- suggestion.txt (issue ledger with 12 entries)
- suggestions_done.txt (change ledger with applied changes)

**Rationale:** These files document the project's professional framing and transformation process for portfolio readiness. This represents the final polish that makes the project portfolio-grade.

---

## Development Timeline (Conceptual)

If this were a real development process, the timeline might look like:

1. **Day 1:** Initial setup and configuration (Steps 01-03)
2. **Day 2-3:** Data acquisition and initial notebook (Steps 04-05)
3. **Day 3:** Path bug discovery and hotfix (Step 06)
4. **Day 4:** Statistical enhancement with FDR (Step 07)
5. **Day 5-6:** Clustering analysis implementation (Steps 08-09)
6. **Day 7:** Documentation enhancement (Step 10)
7. **Day 8:** Final portfolio polish (Step 11)

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

### Path Design Decision (Learned from Bug)
After the initial path bug in step 05, settled on relative paths with clear working directory documentation:
- Simple and maintainable
- Works consistently when run from documented location (code/)
- Avoids complexity of dynamic path resolution
- Clearly documented in README and notebook comments

This decision came after experiencing the pitfall of absolute paths in step 05.

---

## Final State

The final repository (Step 11) represents a portfolio-ready project with:
- ✅ Professional naming (no academic terminology)
- ✅ Clean, well-documented code
- ✅ Comprehensive README with troubleshooting
- ✅ Reproducible analysis (requirements.txt)
- ✅ Clear project identity
- ✅ Proper .gitignore
- ✅ Complete metadata documentation
- ✅ Realistic development history with course corrections

---
