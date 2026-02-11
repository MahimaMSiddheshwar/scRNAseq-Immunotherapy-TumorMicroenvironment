# Characterization of Melanoma Tumor Microenvironment During Anti-PD1 Therapy

**Author:** Mahima M.S. | **Date:** February 2025 | **Dataset:** GSE134388 (TISCH)

---

## Abstract

This study presents comprehensive single-cell analysis of 3,632 cells from a melanoma patient undergoing anti-PD1 immunotherapy (GSE134388, TISCH). Using Python/Scanpy, we identified distinct immune populations including CD8+ T-cells, Tregs, B-cells, and myeloid cells alongside malignant melanoma. Key markers include cytotoxic genes (GZMB, IFNG), checkpoint molecules (PDCD1, LAG3), and melanoma oncogenes (SOX10, MITF, MLANA). Post-treatment sampling captured therapy-induced cellular states, revealing persistent exhaustion and immunosuppression. This analysis establishes a framework for understanding treatment response mechanisms in checkpoint inhibitor therapy.

**Keywords:** scRNA-seq, melanoma, anti-PD1, TISCH, tumor microenvironment

---

## 1. Introduction

### 1.1 The TISCH Database

The **Tumor Immune Single-Cell Hub (TISCH)** provides curated, standardized single-cell datasets exclusively for tumor immunology. Unlike general repositories, TISCH offers harmonized expression matrices, quality-controlled metadata, pre-computed annotations, and interactive visualizations. TISCH's five core objectives are: (1) data harmonization across diverse sources, (2) rigorous quality curation including doublet removal, (3) comprehensive metadata integration, (4) accessibility for researchers, and (5) enabling comparative meta-analyses.

### 1.2 Melanoma and Anti-PD1 Therapy

Melanoma represents an ideal model for immunotherapy research due to high mutational burden and well-characterized responses to checkpoint inhibitors. However, only 30-40% of patients achieve durable responses, creating an urgent need to understand cellular determinants of response at single-cell resolution. The tumor microenvironment comprises malignant cells, immune cells, stromal cells, and endothelial cells—each contributing to treatment outcomes.

### 1.3 Post-Treatment Analysis Rationale

This study analyzes **Dataset GSE134388** (3,632 cells) post-treatment to capture therapy-induced cellular reprogramming. Anti-PD1 therapy reactivates exhausted T-cells and modulates immune interactions. Post-treatment samples reveal: (a) which cells persist during therapy, (b) how exhaustion states change, (c) resistance mechanisms, and (d) early response biomarkers. While single-patient analysis provides deep resolution, multi-patient validation is needed for statistical generalizability.

---

## 2. Materials and Methods

### 2.1 Data Acquisition

From TISCH: `SKCM_GSE134388_aPD1_expression.h5` (37 MB, 3,632 cells × 14,705 genes) and metadata TSV (382 KB) with pre-computed UMAP coordinates and cell type annotations.

### 2.2 Computational Pipeline

**Environment:** Python 3.11, Scanpy 1.9+

1. **Data Loading:** Parsed HDF5, built sparse matrix, created AnnData
2. **Quality Control:** Mean 1,096 genes/cell, 1,988 UMIs/cell, 1.98% mitochondrial
3. **Normalization:** Total count (10,000) + log1p transformation
4. **HVG Selection:** 2,000 highly variable genes (Seurat v3)
5. **Dimensionality:** PCA (50 components, retained 30) + UMAP
6. **Clustering:** KNN (k=15) + Leiden algorithm
7. **Marker Analysis:** Wilcoxon rank-sum test + canonical marker matching

---

## 3. Results

### 3.1 Cellular Composition

UMAP revealed distinct populations:

**Immune Cells:**
- CD8+ T-cells: CD8A, CD8B, GZMB, IFNG, PRF1
- Tregs: CD4, FOXP3, IL2RA, CTLA4
- B-cells: CD19, MS4A1, CD79A
- Myeloid: CD14, CSF1R, LYZ

**Malignant:**
- Melanoma: SOX10, MITF, MLANA, PMEL

### 3.2 Key Markers

**Cytotoxic:** GZMB (apoptosis induction), IFNG (Th1 cytokine, correlates with response), PRF1 (pore-forming, essential for killing)

**Exhaustion:** PDCD1/PD1 (primary anti-PD1 target), LAG3 (marks exhausted cells, poor response predictor)

**Melanoma:** SOX10 (diagnostic), MITF (oncogene), MLANA (immunotherapy target)

### 3.3 T-Cell Heterogeneity

CD8+ T-cells showed mixed states: effector (GZMB+, IFNG+) coexisting with exhausted (PDCD1+, LAG3+). This suggests partial response—some reactivation while others remain refractory, explaining variable clinical outcomes.

### 3.4 Persistent Immunosuppression

Tregs persisted during therapy, indicating ongoing suppression via IL-2 competition (CD25), CTLA4 inhibition, and IL-10/TGF-β secretion. This suggests anti-PD1 monotherapy may be insufficient, supporting combination approaches.

---

## 4. Discussion

### 4.1 Post-Treatment Analysis Significance

Analysis of post-treatment samples provides unique insights into dynamic anti-tumor immunity during checkpoint therapy. Unlike pre-treatment biopsies capturing baseline states, post-treatment samples reveal immediate consequences of PD1 blockade—both successful T-cell reactivation and persistent refractory populations.

The coexistence of effector (GZMB+, IFNG+) and exhausted (PDCD1+, LAG3+) CD8+ T-cells suggests a **partial response** pattern. This heterogeneity aligns with clinical observations of mixed responses rather than complete elimination or total failure. Some T-cells regained function while others remained dysfunctional despite therapy.

### 4.2 Persistent Immunosuppression Implications

Tregs (FOXP3+, IL2RA+, CTLA4+) persisting during anti-PD1 therapy have significant clinical implications. Their suppression mechanisms include: (1) IL-2 sequestration via CD25, starving effector T-cells; (2) CTLA4-mediated inhibition of antigen presentation; (3) immunosuppressive cytokine secretion (IL-10, TGF-β).

This finding supports **combination therapy rationale**. Anti-PD1 plus anti-CTLA4 (ipilimumab) shows improved response rates, potentially through Treg depletion. Novel strategies targeting CD25 (daclizumab) could enhance efficacy in high-Treg tumors.

### 4.3 Melanoma Immune Evasion

Malignant cells (SOX10+, MITF+, MLANA+) persisted despite immune infiltration, suggesting active evasion. Melanoma downregulates antigen presentation, expresses PDL1/PDL2, and secretes suppressive factors. MLANA expression provides immunotherapy targets (TIL therapy, TCR-engineered T-cells), but antigen persistence during therapy suggests recognition alone is insufficient—needing strategies enhancing cytotoxicity or targeting additional vulnerabilities.

### 4.4 Single-Patient Analysis: Value and Limitations

**Strengths:** Unprecedented resolution of intra-tumoral heterogeneity, hypothesis generation for larger cohorts, pipeline validation, and patient-specific immune context understanding.

**Limitations:** Without clinical outcomes, we cannot correlate features with efficacy. Predominantly exhausted T-cells with high Tregs might represent either non-responders or partial responders. Longitudinal sampling (pre-, early on-treatment, progression) would clarify cellular dynamics and clinical relationships.

### 4.5 Future Research Directions

**Predictive Biomarkers:** Do exhausted/effector T-cell ratios or Treg proportions predict response? Multi-patient cohorts (e.g., GSE120575 with 33 patients) could validate these signatures.

**Resistance Mechanisms:** Are PD1+TIM3+LAG3+ signatures enriched in non-responders? Longitudinal studies tracking these markers could predict acquired resistance.

**Combination Therapies:** Would Treg targeting enhance anti-PD1 efficacy? Preclinical models testing anti-CTLA4 or Treg depletion are warranted.

**Spatial Organization:** Do Tregs colocalize with effector T-cells, inhibiting function? Spatial transcriptomics (10X Visium) could reveal proximity-dependent suppression.

**Neoantigen Presentation:** Do melanoma cells express immunogenic neoantigens? WES integration could identify tumor-specific mutations and assess antigen presentation, guiding personalized immunotherapy.

### 4.6 Methodological Considerations

TISCH's curated resources ensured reproducibility, but pre-computed annotations may introduce bias. Independent validation via flow cytometry or IHC would strengthen findings. While Scanpy represents best
