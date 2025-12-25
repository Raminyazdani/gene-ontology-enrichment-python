# Portfolio-Readiness Transformation Report

This report logs all exploration, analysis, changes, and verification steps taken to transform the repository into a portfolio-ready project.

---

## Phase 0: Initial Self-Setup

### 0.1 Created Required Files
- Created `report.md` (this file)
- Will create `suggestion.txt`, `suggestions_done.txt`, `project_identity.md`

### 0.2 Copilot Guidance Files
- `.github/copilot-instructions.md` exists (no changes needed)

---

## Phase 1: Understanding the Project

### 1.1 Repository Exploration

**Discovered Structure:**
```
/
├── .github/
│   ├── copilot-instructions.md
│   └── ISSUE_TEMPLATE/
├── code/
│   ├── assignment_4_1.ipynb        # CD-HIT clustering analysis (appears unrelated to GO)
│   ├── assignment_4_2.ipynb        # GO enrichment analysis (main focus)
│   ├── ex2.tsv                     # Protein set (118 IDs)
│   ├── goa_arabidopsis.tsv         # GO annotations (~159k rows)
│   ├── quickgo_term_info.tsv       # GO term metadata
│   └── content/                    # FASTA files and clustering outputs
├── requirements.txt
└── README.md
```

**Domain & Problem:**
- Performs Gene Ontology (GO) enrichment analysis on Arabidopsis thaliana protein sets
- Uses Fisher's exact test with FDR correction to identify overrepresented GO terms
- Processes GO annotations from UniProt GOA database

**Stack:**
- Python 3.x
- Jupyter Notebooks
- pandas, numpy, scipy (Fisher exact test), statsmodels (FDR), requests
- GO annotation data from QuickGO/GOA

**Current Naming Issues Found:**
1. README mentions "pobd4/" folder (doesn't exist; academic course folder name)
2. Notebooks named "assignment_4_1.ipynb" and "assignment_4_2.ipynb" (academic naming)
3. Notebooks contain academic headers (Prof name, matriculation numbers, due dates, course info)
4. assignment_4_1.ipynb appears to be about CD-HIT clustering, not GO enrichment (possibly mismatched content)
5. Relative paths use "./" which assumes running from code/ directory

**How it Runs:**
- Notebooks run from code/ directory
- Uses relative paths: "./ex2.tsv", "./goa_arabidopsis.tsv"
- assignment_4_2.ipynb is the main GO enrichment notebook
- assignment_4_1.ipynb appears focused on sequence clustering (CD-HIT)

---
