# Forensic-QC-Audit-EGCG-Mediated-Senescence-Reversal

This repository contains the complete reproducibility pipeline and quality-control re-analysis for the RNA-seq dataset **GSE286438**. This project was conducted as part of the **DH607 (Introduction to Computational Multiomics)** course under **Professor Saket Choudhary**, Koita Centre for Digital Health (KCDH), IIT Bombay.

## Project Overview

The objective of this project is to **forensically audit the gene expression evidence** supporting the claim that **Epigallocatechin gallate (EGCG)** reverses cellular senescence. 

In the original study, it was claimed that EGCG treatment reverses senescence-associated transcriptional signatures. This re-analysis independently evaluates the robustness of those claims by examining data integrity, sample clustering, and the statistical significance of differential expression.



---

## Dataset Profile

- **Source:** [NCBI GEO GSE286438](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE286438) / [PMC11790594](https://pmc.ncbi.nlm.nih.gov/articles/PMC11790594/)
- **Data Type:** Bulk RNA-seq
- **Experimental Groups:**
  - **NT (Normal/Control):** Healthy, proliferating cells.
  - **SEN (Senescent):** Cells induced into a senescent state.
  - **ST (Senescent + EGCG Treatment):** Senescent cells treated with EGCG to test for reversal.

---

## Methodology & Pipeline

### 1. Quality Control & Exploratory Data Analysis
- **Normalization:** Log-transformation and library size normalization.
- **Sample Integrity:** Evaluated using Pearson correlation matrices and Principal Component Analysis (PCA) to assess group clustering and potential outliers.

### 2. Differential Gene Expression (DGE)
- **Pipeline:** Implemented using **PyDESeq2** for robust statistical modeling.
- **Thresholds:** Adjusted $p$-value $< 0.05$ and $|\log_2 \text{Fold Change}| \geq 1$.
- **Contrasts:** - `SEN vs NT` (Quantifying the senescent phenotype)
  - `ST vs SEN` (Evaluating treatment efficacy)
  - `ST vs NT` (Assessing how closely treated cells resemble normal cells)

### 3. Biomarker Validation
- Targeted analysis of canonical markers including **SASP** (Senescence-Associated Secretory Phenotype) factors and proliferation-associated genes ($p21$, $p16$, $Ki67$).

---

## Audit Findings

Our forensic re-analysis revealed several critical points that challenge or qualify the original study's narrative:

1. **Incomplete Transcriptional Reversal:** The EGCG-treated group (**ST**) showed only partial movement back toward the control state (**NT**).
2. **Persistent Senescence Markers:** Several key biomarkers associated with senescence remained significantly upregulated even after EGCG treatment.
3. **Condition Mixing:** PCA and correlation analysis revealed partial mixing between **ST** and **SEN** samples, suggesting that the treatment effect may not be strong enough to clearly separate the groups transcriptomically.
4. **Statistical Scrutiny:** Re-analysis via `PyDESeq2` identified fewer significant genes in the `ST vs SEN` contrast than might be expected for a "complete reversal" of phenotype.



---

## Repository Structure

- `GSE286438_Counts_matrix_Patel_2024.csv`: The raw count matrix used for analysis.
- `phase1.ipynb`: Initial EDA, QC, and correlation analysis.
- `Differential Gene Expression.ipynb`: Main DGE pipeline and functional enrichment.



1. **Clone the repository:**
   ```bash
   git clone [https://github.com/](https://github.com/)[Your-Username]/Forensic-QC-Audit-EGCG-Mediated-Senescence-Reversal.git
