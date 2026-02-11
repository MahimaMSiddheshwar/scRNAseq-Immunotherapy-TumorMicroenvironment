# Characterization of the Melanoma Tumor Microenvironment in Anti-PD1 Therapy
## A Single-Cell Transcriptomic Analysis Using TISCH Database Resources

**Author:** Mahima M.S.  
**Date:** February 2025  
**Dataset:** GSE134388 from TISCH Database

---

## Abstract

This study presents a comprehensive computational analysis of 3,632 single cells from a melanoma patient undergoing anti-PD1 immunotherapy, accessed through the TISCH database. Using Python/Scanpy, we identified distinct immune cell populations and characterized the tumor microenvironment during active therapy.

---

## 1. Introduction

### 1.1 The TISCH Database

The **Tumor Immune Single-Cell Hub (TISCH)** (http://tisch.comp-genomics.org/) is a specialized bioinformatics resource exclusively dedicated to tumor immunology research. Unlike general repositories like GEO, TISCH provides:

**Core Objectives:**
1. **Data Harmonization:** Standardizing diverse single-cell datasets into analysis-ready formats
2. **Quality Curation:** Rigorous QC including doublet removal and batch correction
3. **Metadata Integration:** Comprehensive annotations (cell types, patient info, treatment status)
4. **Accessibility:** Lowering technical barriers for complex single-cell analysis
5. **Comparative Analysis:** Enabling cross-study comparisons through consistent formatting

**Why TISCH Matters:**
TISCH addresses the challenge of data heterogeneity by curating tumor single-cell data into a unified framework, making it invaluable for computational biologists studying cancer immunology.

### 1.2 Dataset Selection: GSE134388

**Selected Dataset:** GSE134388 - Melanoma Anti-PD1 Therapy
- **Source:** TISCH Database
- **Cancer Type:** Skin Cutaneous Melanoma (SKCM)
- **Treatment:** Anti-PD1 immunotherapy (pembrolizumab/nivolumab)
- **Cells:** 3,632 high-quality single cells
- **Genes:** 14,705 genes
- **Platform:** 10X Genomics

### 1.3 Why Post-Treatment (Not Pre-Treatment) Data?

**Critical Research Rationale:**

1. **Captures Therapy-Induced Changes:**
   - Anti-PD1 fundamentally alters the tumor microenvironment
   - Post-treatment samples show reactivated T-cells and therapy effects
   - Pre-treatment cannot show these dynamic changes

2. **Understanding Response Mechanisms:**
   - Reveals which cells persist during therapy
   - Shows therapy-refractory vs. responsive populations
   - Captures exhaustion states modulated by PD1 blockade

3. **Resistance Investigation:**
   - Identifies exhausted T-cells refractory to reactivation
   - Reveals immunosuppressive Tregs limiting therapy
   - Shows melanoma-intrinsic immune evasion

4. **Biomarker Discovery:**
   - Post-treatment signatures predict long-term response
   - Early indicators before radiographic evidence

**Limitation Acknowledged:** Single-patient data provides deep resolution but requires multi-patient validation for statistical conclusions.

---

## 2. Research Questions & Hypotheses

### Primary Research Questions:

**Q1:** What is the cellular composition (CD8+ T-cells, Tregs, B-cells, myeloid cells) vs. malignant cells during anti-PD1 therapy?

**Q2:** Do we observe distinct T-cell states (effector vs. exhausted) and their transcriptional signatures?

**Q3:** Are regulatory T-cells present, contributing to immunosuppression despite therapy?

**Q4:** Which cells express PD1 and other checkpoint molecules?

**Q5:** What distinguishes malignant melanoma cells from immune cells?

### Testable Hypotheses:

- **H1:** Mixed CD8+ T-cell states (effector + exhausted) will be present
- **H2:** PD1 expression will mark terminally exhausted T-cells
- **H3:** Tregs will persist, indicating ongoing immunosuppression
- **H4:** Melanoma cells will show immune evasion signatures

---

## 3. Methods

### 3.1 Data from TISCH

**Downloaded Files:**
1. `SKCM_GSE134388_aPD1_expression.h5` (37 MB) - Expression matrix
2. `SKCM_GSE134388_aPD1_CellMetainfo_table.tsv` (382 KB) - Cell metadata

**TISCH Metadata Includes:**
- Cell barcodes and UMAP coordinates
- Cell types (malignancy, major/minor lineage)
- Patient and sample IDs
- Pre-computed annotations

### 3.2 Computational Pipeline (Python/Scanpy)

**Step 1: Data Loading**
- Parsed HDF5 using h5py
- Built sparse matrix: 3,632 cells × 14,705 genes
- Created AnnData object with integrated metadata

**Step 2: Quality Control**
- Calculated QC metrics:
  - n_genes_by_counts (genes per cell)
  - total_counts (UMIs per cell)
  - pct_counts_mt (mitochondrial %)
- **Results:** Mean 1,096 genes, 1,988 UMIs, 1.98% mitochondrial (excellent quality)

**Step 3: Normalization**
- Total count normalization (10,000 counts)
- Log1p transformation
- Preserved raw counts for differential expression

**Step 4: Feature Selection**
- Selected 2,000 Highly Variable Genes (HVGs)
- Method: Seurat v3 variance stabilization

**Step 5: Dimensionality Reduction**
- PCA: 50 components
- UMAP: n_neighbors=15, visualization

**Step 6: Clustering**
- KNN graph (k=15)
- Leiden algorithm for community detection

**Step 7: Marker Analysis**
- Wilcoxon rank-sum test for differential expression
- Cell type annotation using canonical markers

---

## 4. Results

### 4.1 Cell Populations Identified

**Immune Cells:**

**1. Cytotoxic CD8+ T-Cells (Predominant)**
- **Markers:** CD8A, CD8B, GZMB, IFNG, PRF1
- **Significance:** Effector anti-tumor immunity through direct killing

**2. Regulatory CD4+ T-Cells (Tregs)**
- **Markers:** CD4, FOXP3, IL2RA, CTLA4
- **Significance:** Immunosuppressive population limiting therapy efficacy

**3. B-Lymphocytes**
- **Markers:** CD19, MS4A1, CD79A
- **Significance:** Antibody production and antigen presentation

**4. Myeloid Cells**
- **Markers:** CD14, CD68, CSF1R, LYZ
- **Significance:** Phagocytosis and cytokine production

**Malignant Cells:**

**Melanoma Cells**
- **Markers:** SOX10, MITF, MLANA, PMEL, TYR
- **Significance:** Melanocyte-derived cancer cells

### 4.2 Key Marker Genes & Biological Significance

#### Cytotoxic Markers:

**GZMB (Granzyme B)**
- **Function:** Serine protease in cytotoxic granules
- **Mechanism:** Induces apoptosis in target cells
- **Significance:** High expression = active anti-tumor function

**IFNG (Interferon-gamma)**
- **Function:** Critical Th1 cytokine
- **Mechanism:** Activates macrophages, enhances antigen presentation
- **Significance:** Correlates with immunotherapy response

**PRF1 (Perforin)**
- **Function:** Pore-forming protein
- **Mechanism:** Enables granzyme entry into targets
- **Significance:** Essential for T-cell-mediated killing

#### Exhaustion Markers:

**PDCD1 (PD1)**
- **Function:** Inhibitory receptor on T-cells
- **Mechanism:** Binds PDL1/PDL2 to inhibit activation
- **Significance:** Primary target of pembrolizumab/nivolumab

**LAG3**
- **Function:** Inhibitory receptor
- **Significance:** Marks exhausted T-cells; associated with poor response

#### Melanoma Markers:

**SOX10**
- **Function:** Master melanocyte transcription factor
- **Significance:** Diagnostic marker; maintained in melanoma

**MITF**
- **Function:** Regulates melanocyte survival
- **Significance:** Critical melanoma oncogene

**MLANA (Melan-A)**
- **Function:** Melanocyte differentiation antigen
- **Significance:** Widely used melanoma marker and immunotherapy target

### 4.3 T-Cell Heterogeneity

**Two Distinct CD8+ T-Cell States:**

1. **Effector T-Cells:**
   - Express GZMB, IFNG, PRF1
   - Active cytotoxic capacity
   - Likely responding to therapy

2. **Exhausted T-Cells:**
   - Express PDCD1, LAG3
   - Reduced cytotoxic markers
   - May be therapy-refractory

**Implication:** Anti-PD1 reactivates some exhausted cells while others remain refractory, explaining variable clinical responses.

### 4.4 Regulatory T-Cells Persist

**Treg Presence:**
- Constitute significant population despite therapy
- Express FOXP3, IL2RA, CTLA4
- Indicating ongoing immunosuppression

**Mechanisms of Suppression:**
1. IL-2 competition (via CD25)
2. CTLA4-mediated inhibition
3. Secretion of IL-10 and TGF-β
4. Direct cytotoxicity of effector cells

---

## 5. Discussion

### 
