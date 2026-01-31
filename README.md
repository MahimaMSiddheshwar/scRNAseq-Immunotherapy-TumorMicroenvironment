# Single-Cell RNA-seq Analysis of Anti–PD-1 Treated Melanoma (SKCM)

<p align="center">
  <img src="https://img.shields.io/badge/Single--Cell%20RNA--seq-Scanpy-blue" />
  <img src="https://img.shields.io/badge/Language-Python%203.11-green" />
  <img src="https://img.shields.io/badge/Editor-VS%20Code-blue" />
  <img src="https://img.shields.io/badge/Version%20Control-Git%20%7C%20GitHub-black" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-orange" />
</p>

---

## Project Title 

**End-to-End Single-Cell RNA-seq Analysis of Anti–PD-1 Treated Melanoma Tumor (SKCM_GSE115978_aPD1)**

---

## Project Overview

This project presents a complete, end-to-end **single-cell RNA sequencing (scRNA-seq)** analysis of a melanoma (SKCM) tumor sample treated with **anti–PD-1 immunotherapy**, derived from the **TISCH** database (dataset: `SKCM_GSE115978_aPD1`).

The analysis focuses on:

* Characterizing the **tumor immune microenvironment**
* Identifying major **immune and stromal cell populations**
* Annotating clusters using **canonical marker genes**
* Building a **reproducible and interpretable scRNA-seq workflow** suitable for research, interviews, and presentations

---

## Dataset Description

* **Source**: TISCH (Tumor Immune Single Cell Hub)
* **Original GEO Accession**: GSE115978
* **Sample Type**: Melanoma (SKCM)
* **Treatment**: Anti–PD-1 (aPD1)
* **Number of Patients**: 1
* **Sample Composition**:

  * Single tumor sample
  * No matched normal tissue
  * No batch effects

This makes the dataset ideal for **within-sample clustering and immune profiling**, without the need for batch correction or multi-patient integration.

---

## 🛠️ Tech Stack & Skills Used

### 🔹 Programming & Environment

* **Python 3.11**
* **VS Code** (Jupyter Notebook workflow)
* **Virtual Environment (`venv`)**
* **Git & GitHub** (version control)

### 🔹 Core Single-Cell Libraries

* **Scanpy** – scRNA-seq analysis framework
* **AnnData** – structured single-cell data container
* **NumPy / Pandas** – numerical & tabular processing
* **Matplotlib / Seaborn** – visualization
* **SciPy / scikit-learn** – PCA, neighbors graph

### 🔹 Analysis Methods

* Quality control (QC filtering)
* Log-normalization
* Highly Variable Gene (HVG) selection
* Principal Component Analysis (PCA)
* KNN graph construction
* **UMAP** dimensionality reduction
* **Leiden clustering**
* Wilcoxon rank-sum test for marker genes
* Cell-type annotation using canonical markers

---

## 📁 Project Structure

```text
scRNAseq_Immunotherapy/
│
├── data/
│   ├── raw/                     # Original input data
│   └── processed/               # Intermediate & final .h5ad files
│
├── scripts/                     # Stepwise analysis notebooks
│   ├── 01_load_and_check.ipynb
│   ├── 02_qc_and_filtering.ipynb
│   ├── 03_normalization_hvg_pca.ipynb
│   ├── 04_neighbors_umap_clustering.ipynb
│   └── 05_marker_genes_annotation.ipynb
│
├── results/
│   ├── umap/                    # QC & clustering UMAPs
│   └── markers/                 # Marker tables & expression plots
│
├── docs/                        # Reports (.Rmd / exports)
├── README.md
└── .gitignore
```

---

## Analysis Workflow (End-to-End)

### 1️⃣ Data Ingestion

* Loaded preprocessed scRNA-seq data into **AnnData (.h5ad)** format
* Verified cell counts, gene counts, metadata fields

### 2️⃣ Quality Control (QC)

* Metrics used:

  * Total counts per cell
  * Number of genes per cell
  * Mitochondrial gene percentage
* Removed low-quality and outlier cells

### 3️⃣ Normalization & Feature Selection

* Log-normalized expression values
* Identified **Highly Variable Genes (HVGs)**
* Scaled data for downstream PCA

### 4️⃣ Dimensionality Reduction

* **PCA** for noise reduction and structure capture
* **UMAP** for 2D visualization (UMAP1 / UMAP2)

### 5️⃣ Graph Construction & Clustering

* Built K-nearest neighbor graph
* Applied **Leiden clustering** (resolution = 0.5)
* Resulted in **14 clusters (0–13)**

### 6️⃣ Marker Gene Detection

* Differential expression: **Wilcoxon rank-sum test**
* Strategy: *cluster vs. rest*
* Generated:

  * Top 50 marker genes per cluster (CSV)
  * Heatmaps and dotplots

### 7️⃣ Cell-Type Annotation

* Annotated clusters using known marker genes:

  * T cells (CD3D, CD3E, TRAC)
  * B cells (MS4A1, CD79A)
  * NK cells (NKG7, GNLY)
  * Myeloid (LYZ, LST1)
  * Endothelial (PECAM1, VWF)
  * Fibroblasts (DCN, COL1A1)
  * Tumor / Melanoma (EPCAM, KRTs)
* Final labeled UMAP with clean visualization

---

## Key Outputs

* **UMAP plots** (QC, clusters, cell types)
* **Marker gene tables** (CSV)
* **Heatmaps & dotplots** for marker validation
* **Final annotated AnnData object**

---

## Key Takeaways

* Clear separation of **immune, stromal, and tumor populations**
* Successful annotation of major immune cell types
* Robust, reproducible scRNA-seq pipeline
* Analysis suitable for **research presentation and interviews**

---

## Author

**Mahima Mahabaleshwar Siddheshwar**
Bioinformatics Scientist | scRNA-seq | Transcriptomics | Immunogenomics

---

This repository is designed for:

* Learning and demonstration of scRNA-seq workflows 🧬
* Interview discussions and project presentations
* Extension to multi-sample or multi-patient analyses

---

⭐ If you find this project useful, feel free to star the repository.
