# Top 5 Marker Genes Per Cluster - Melanoma Anti-PD1 Analysis

**Dataset:** GSE134388 from TISCH Database  
**Analysis Date:** January 30, 2025  
**Total Clusters Identified:** 14  
**Method:** Wilcoxon rank-sum test, top 50 markers per cluster

---

## Cluster 0: Perivascular/Stromal Cells (n=511 cells)

**Top 5 Marker Genes:**

1. **TAGLN** (Transgelin)
   - Full Name: Smooth muscle protein 22-alpha
   - Function: Smooth muscle marker, regulates cytoskeleton
   - Expression: 95.6% of cells in cluster, log2FC = 5.59
   - Cell Type: Perivascular smooth muscle cells/pericytes

2. **ACTA2** (Alpha-smooth muscle actin)
   - Full Name: Actin, alpha 2, smooth muscle
   - Function: Contractile apparatus of smooth muscle
   - Expression: 94.0% of cells, log2FC = 5.59
   - Cell Type: Myofibroblasts, pericytes

3. **CALD1** (Caldesmon)
   - Full Name: Caldesmon 1
   - Function: Calcium-regulated smooth muscle contraction
   - Expression: 99.5% of cells, log2FC = 3.46
   - Cell Type: Smooth muscle cells

4. **IGFBP7** (Insulin-like growth factor binding protein 7)
   - Full Name: IGFBP7
   - Function: Endothelial cell marker, angiogenesis regulator
   - Expression: 99.0% of cells, log2FC = 3.40
   - Cell Type: Endothelial cells, pericytes

5. **ADIRF** (Adipogenesis regulatory factor)
   - Full Name: C10orf10/ADIRF
   - Function: Adipocyte differentiation, stromal marker
   - Expression: 98.3% of cells, log2FC = 3.64
   - Cell Type: Stromal fibroblasts

**Biological Interpretation:** This cluster represents perivascular mural cells (pericytes) and stromal fibroblasts that support tumor vasculature and extracellular matrix.

---

## Cluster 1: T-Lymphocytes (n=437 cells) - DOMINANT IMMUNE POPULATION

**Top 5 Marker Genes:**

1. **CD3D** (CD3 delta subunit)
   - Full Name: CD3d molecule, delta (CD3-TCR complex)
   - Function: T-cell receptor signaling, T-cell identity
   - Expression: 76.0% of cells, log2FC = 5.32
   - Cell Type: All T-lymphocytes (pan-T-cell marker) ⭐

2. **B2M** (Beta-2-microglobulin)
   - Full Name: Beta-2-microglobulin
   - Function: MHC Class I light chain, antigen presentation
   - Expression: 100% of cells, log2FC = 0.76
   - Cell Type: All nucleated cells (high in lymphocytes)

3. **CD52** (CD52 molecule)
   - Full Name: CAMPATH-1 antigen
   - Function: T-cell surface glycoprotein, therapeutic target
   - Expression: 91.2% of cells, log2FC = 4.88
   - Cell Type: T and B lymphocytes

4. **RPS29** (Ribosomal protein S29)
   - Full Name: Ribosomal protein S29
   - Function: Protein synthesis (elevated in lymphocytes)
   - Expression: 99.9% of cells, log2FC = 0.87
   - Cell Type: Highly expressed in immune cells

5. **IL32** (Interleukin 32)
   - Full Name: Interleukin 32
   - Function: Pro-inflammatory cytokine, NK/T-cell activation
   - Expression: 87.1% of cells, log2FC = 5.03
   - Cell Type: Activated T-cells and NK cells

**Biological Interpretation:** This is the dominant T-cell population infiltrating the melanoma tumor, representing adaptive immune response during anti-PD1 therapy.

---

## Cluster 2: Cancer-Associated Fibroblasts (n=188 cells)

**Top 5 Marker Genes:**

1. **DCN** (Decorin)
   - Full Name: Decorin
   - Function: Extracellular matrix proteoglycan, tumor suppressor
   - Expression: 99.1% of cells, log2FC = 3.90
   - Cell Type: Stromal fibroblasts

2. **CXCL14** (C-X-C motif chemokine ligand 14)
   - Full Name: Chemokine (C-X-C motif) ligand 14
   - Function: Chemoattractant for immune cells
   - Expression: 91.7% of cells, log2FC = 4.54
   - Cell Type: Fibroblasts (CAFs)

3. **FBLN1** (Fibulin-1)
   - Full Name: Fibulin 1
   - Function: Extracellular matrix glycoprotein
   - Expression: 83.8% of cells, log2FC = 5.23
   - Cell Type: Fibroblasts, basement membrane

4. **VCAN** (Versican)
   - Full Name: Versican
   - Function: Chondroitin sulfate proteoglycan, ECM component
   - Expression: 88.9% of cells, log2FC = 4.21
   - Cell Type: Cancer-associated fibroblasts (CAFs)

5. **CCDC80** (Coiled-coil domain containing 80)
   - Full Name: CCDC80/URB/SSG1
   - Function: Adipocyte differentiation, stromal marker
   - Expression: 91.7% of cells, log2FC = 3.33
   - Cell Type: Fibroblasts

**Biological Interpretation:** Cancer-associated fibroblasts (CAFs) that remodel the extracellular matrix and modulate tumor microenvironment during immunotherapy.

---

## Cluster 3: Myeloid/Antigen-Presenting Cells (n=342 cells)

**Top 5 Marker Genes:**

1. **LYZ** (Lysozyme)
   - Full Name: Lysozyme
   - Function: Antibacterial enzyme, macrophage marker ⭐
   - Expression: 98.2% of cells, log2FC = 6.09
   - Cell Type: Macrophages, monocytes ⭐

2. **HLA-DPB1** (MHC Class II DP beta 1)
   - Full Name: Major histocompatibility complex, class II, DP beta 1
   - Function: Antigen presentation to CD4+ T-cells ⭐
   - Expression: 100% of cells, log2FC = 4.98
   - Cell Type: Professional antigen-presenting cells ⭐

3. **HLA-DPA1** (MHC Class II DP alpha 1)
   - Full Name: Major histocompatibility complex, class II, DP alpha 1
   - Function: Antigen presentation ⭐
   - Expression: 100% of cells, log2FC = 5.22
   - Cell Type: Dendritic cells, macrophages, B-cells ⭐

4. **HLA-DRA** (MHC Class II DR alpha)
   - Full Name: Major histocompatibility complex, class II, DR alpha
   - Function: Antigen presentation to CD4+ T-cells ⭐
   - Expression: 100% of cells, log2FC = 5.10
   - Cell Type: Professional APCs (macrophages, DCs, B-cells) ⭐

5. **HLA-DQA1** (MHC Class II DQ alpha 1)
   - Full Name: Major histocompatibility complex, class II, DQ alpha 1
   - Function: Antigen presentation ⭐
   - Expression: 98.2% of cells, log2FC = 5.71
   - Cell Type: Antigen-presenting cells ⭐

**Biological Interpretation:** Professional antigen-presenting cells (likely macrophages and dendritic cells) that present tumor antigens to T-cells during anti-PD1 therapy.

---

## Cluster 4: Collagen-Producing Fibroblasts (n=321 cells)

**Top 5 Marker Genes:**

1. **COL1A1** (Collagen Type I Alpha 1)
   - Full Name: Collagen, type I, alpha 1
   - Function: Major structural collagen of ECM
   - Expression: 98.1% of cells, log2FC = 2.79
   - Cell Type: Fibroblasts (matrix-producing)

2. **COL3A1** (Collagen Type III Alpha 1)
   - Full Name: Collagen, type III, alpha 1
   - Function: Reticular fiber component
   - Expression: 98.1% of cells, log2FC = 2.56
   - Cell Type: Fibroblasts

3. **COL6A1** (Collagen Type VI Alpha 1)
   - Full Name: Collagen, type VI, alpha 1
   - Function: Beaded filament collagen
   - Expression: 96.9% of cells, log2FC = 3.08
   - Cell Type: Fibroblasts

4. **COL1A2** (Collagen Type I Alpha 2)
   - Full Name: Collagen, type I, alpha 2
   - Function: Type I collagen component
   - Expression: 98.1% of cells, log2FC = 2.51
   - Cell Type: Fibroblasts

5. **COL5A2** (Collagen Type V Alpha 2)
   - Full Name: Collagen, type V, alpha 2
   - Function: Regulates collagen fibrillogenesis
   - Expression: 94.4% of cells, log2FC = 3.71
   - Cell Type: Fibroblasts

**Biological Interpretation:** Matrix-producing fibroblasts responsible for dense collagen deposition characteristic of desmoplastic melanoma response.

---

## Cluster 5: Macrophages (n=185 cells)

**Top 5 Marker Genes:**

1. **SEPP1** (Selenoprotein P)
   - Full Name: Selenoprotein P
   - Function: Selenium transport, antioxidant
   - Expression: 100% of cells, log2FC = 4.57
   - Cell Type: Macrophages (especially M2)

2. **RNASE1** (Ribonuclease A Family Member 1)
   - Full Name: Ribonuclease, RNase A family, 1
   - Function: Endoribonuclease, immune regulation
   - Expression: 95.7% of cells, log2FC = 8.44
   - Cell Type: Macrophages

3. **C1QA** (Complement C1q A Chain)
   - Full Name: Complement component 1, q subcomponent, A chain
   - Function: Complement system, clearance of apoptotic cells
   - Expression: 94.1% of cells, log2FC = 7.72
   - Cell Type: Macrophages ⭐

4. **MS4A6A** (Membrane Spanning 4-Domains A6A)
   - Full Name: Membrane-spanning 4-domains, subfamily A, member 6A
  
