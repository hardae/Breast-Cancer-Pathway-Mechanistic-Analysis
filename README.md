# Breast-Cancer-Pathway-Mechanistic-Analysis


A pathway and gene ontology enrichment analysis pipeline identifying biological mechanisms disrupted in breast cancer, built on DEGs from differential expression analysis (Project 1).

---

## Project Overview

Finding differentially expressed genes is only the first step. The deeper biological question is: **what mechanisms do those gene changes actually affect?**

This project takes 1,434 significant DEGs from a limma differential expression analysis (GSE183947) and performs GO and pathway enrichment analysis to identify the biological processes, molecular functions and pathways that are disrupted in breast cancer tumour tissue.

This is **Project 3** in a structured bioinformatics pipeline:

```
Project 1: Differential Expression Analysis (limma, R) ✅
        ↓
Project 2: Subtype Classification (ML, Python) ✅
        ↓
Project 3: Pathway & Mechanistic Analysis (this project) ✅
       
```

---

## Dataset

**Input:** DEGs from Project 1 — GSE183947 breast cancer dataset (29 tumour vs 23 normal samples)

| File | Description |
|------|-------------|
| `breast_cancer_significant_DEGs.csv` | 1,434 significant DEGs from limma (adj.P.Val < 0.05) |
| `breast_cancer_all_results.csv` | Full limma results for all 20,098 genes tested |

**DEG Summary:**
- Total significant DEGs: 1,434
- Upregulated in tumour: 542 genes
- Downregulated in tumour: 892 genes

---

## Pipeline

```
DEGs from Project 1 (CSV input)
        ↓
Load & explore DEG file
        ↓
Separate upregulated (logFC > 0) and downregulated (logFC < 0) genes
        ↓
Extract gene name lists
        ↓
GO Enrichment Analysis — gProfiler (upregulated genes)
        ↓
GO Enrichment Analysis — gProfiler (downregulated genes)
        ↓
Filter significant results & sort by p_value
        ↓
Visualise — Bar plots & Dot plots
        ↓
Biological interpretation
```

---

## Results

### Upregulated Genes (542) — Top Enriched Pathways

| Pathway | -log10(p_value) |
|---------|----------------|
| Mitotic cell cycle process | ~44 |
| Mitotic cell cycle | ~42 |
| Cell cycle process | ~41 |
| Cell cycle | ~35 |
| Cell division | ~32 |
| Chromosome segregation | ~31 |

**Biological interpretation:** Upregulated genes overwhelmingly converge on **cell cycle and proliferation pathways** — the molecular machinery tumour cells hijack to divide uncontrollably.

---

### Downregulated Genes (892) — Top Enriched Pathways

| Pathway | -log10(p_value) |
|---------|----------------|
| Anatomical structure development | ~45 |
| Multicellular organismal process | ~44 |
| Animal organ development | ~44 |
| Developmental process | ~43 |
| Cell migration | ~33 |
| Vasculature development | ~32 |
| Blood vessel development | ~31 |

**Biological interpretation:** Downregulated genes reveal three key mechanisms:
- **Loss of tissue differentiation** — tumour cells losing their normal breast cell identity
- **Angiogenesis** (vasculature/blood vessel development) — tumours building their own blood supply
- **Cell migration/locomotion** — cells becoming motile, a precursor to metastasis

---

### Hallmarks of Cancer Identified

This analysis computationally recapitulates established Hallmarks of Cancer (Hanahan & Weinberg):

- ✅ **Sustaining proliferative signalling** → upregulated cell cycle pathways
- ✅ **Inducing angiogenesis** → downregulated vasculature development terms
- ✅ **Activating invasion and metastasis** → downregulated cell migration terms
- ✅ **Loss of differentiation** → downregulated developmental/morphogenesis terms

---

## Visualisations

| Plot | Description |
|------|-------------|
| `top_15_upregulated_pathways` | Bar plot — top 15 enriched pathways in upregulated genes |
| `top_15_downregulated_pathways` | Bar plot — top 15 enriched pathways in downregulated genes |
| `top_15_upregulated_pathways_scatter` | Dot plot — significance + gene count for upregulated pathways |
| `top_15_downregulated_pathways_scatter` | Dot plot — significance + gene count for downregulated pathways |

---

## Requirements

```
python >= 3.10
pandas
matplotlib
seaborn
gprofiler-official
```

```bash
pip install pandas matplotlib seaborn gprofiler-official
```

---

## How to Run

1. Clone the repository
```bash
git clone https://github.com/hardae/Breast-Cancer-Pathway-Mechanistic-Analysis.git
cd Breast-Cancer-Pathway-Mechanistic-Analysis
```

2. Place your DEG CSV files in the project folder

3. Open and run the notebook top to bottom
```bash
jupyter notebook brca_pathway_analysis.ipynb
```

---

## Connection to Project 1

This project directly continues from Project 1 ([Breast-cancer-Analysis][https://github.com/hardae/breast-cancer-expression-analysis]), using its output DEGs as input. Together they form a complete transcriptomics → mechanism discovery pipeline.

---

## Author

Bioinformatics Intern | IITA Nigeria
MSc Medical Biology and Genetics
