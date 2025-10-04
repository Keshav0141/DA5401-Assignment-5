# DA5401-Assignment-5 Visualizing Data Veracity Challenges in Multi-Label Classification
- Name: Aryan Prasad
- Roll No: DA25M007

## Overview

This project explores **data veracity issues** in the **Yeast dataset**, a benchmark multi-label classification dataset used in bioinformatics.  
The analysis applies two nonlinear dimensionality reduction techniques — **t-SNE** and **Isomap** — to visualize and interpret complex relationships among gene expression features.

The objective is to identify:
- Noisy or ambiguous labels  
- Outliers  
- Hard-to-learn samples  
- Structural patterns within the feature manifold  

The notebook also demonstrates how visual analytics can reveal hidden data quality problems in multi-label datasets.

---

## Dataset Description

- **Dataset:** Yeast Multi-Label Dataset  
- **Samples:** 2,417  
- **Features:** 103 continuous gene expression variables  
- **Labels:** 14 functional categories  

---

## Key Techniques and Workflow

### **Part A — Preprocessing**
- Data loading and dimensionality checks  
- Handling missing or invalid values  
- Label transformation for simplified visualization  
- Feature standardization using `StandardScaler`

### **Part B — t-SNE and Veracity Inspection**
- Application of **t-SNE** for 2D visualization with multiple perplexity values (5, 30, 50, 100)  
- Evaluation metrics:
  - **KL Divergence**
  - **Trustworthiness**
- Visual inspection for:
  - Noisy or ambiguous samples
  - Outliers using Local Outlier Factor (LOF)
  - High-entropy (hard-to-learn) samples
- Graphs include:
  - Metric trends vs. perplexity  
  - Final 2D t-SNE map  
  - Outlier and entropy visualization

### **Part C — Isomap and Global Manifold Analysis**
- Implementation of **Isomap** for global manifold preservation  
- Evaluation metrics:
  - **Reconstruction Error**
  - **Trustworthiness**
- Comparison with t-SNE:
  - Local vs. global preservation
  - Effect of neighborhood size (`n_neighbors`)
- Analysis of manifold curvature and its implication on classification difficulty  

---

## Theoretical Background

The project provides mathematical derivations for both algorithms:
- **t-SNE:**
  - Probability-based local similarity preservation  
  - KL Divergence minimization  
  - Gradient formulation  
- **Isomap:**
  - Geodesic distance computation via neighborhood graphs  
  - Classical MDS on distance matrix  
  - Eigen-decomposition for embedding  

Formulas are included in LaTeX format for clarity and documentation quality.

---

## Results Summary

| Method | Key Metric | Observation |
|:--|:--|:--|
| **t-SNE (Perplexity 30)** | KL ≈ 2.18, Trust ≈ 0.93 | Balanced local and global structure; clear cluster separations |
| **Isomap (n_neighbors 15)** | Recon ≈ 159, Trust ≈ 0.73 | Smooth manifold, strong global continuity |
| **Outliers (LOF)** | ≈ 49 | Sparse edge points with atypical expression patterns |
| **High-Entropy Samples** | ≈ 4 | Very few ambiguous or mixed-label regions |

The visualizations highlight the trade-off between **local precision (t-SNE)** and **global structure (Isomap)** in manifold learning.

---
