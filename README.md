# Forensic-QC-Audit-EGCG-Mediated-SenescenceReversal
This repository contains the complete reproducibility pipeline and quality-control re-analysis for the RNA-seq dataset **GSE286438**, performed as part of my **DH607( Introduction to Computational Multiomics)** course project, under Professor Saket Choudhary, KCDH IIT Bombay. 

The objective of this project is to **forensically audit the gene expression evidence** supporting the claim that **Epigallocatechin gallate (EGCG)** reverses cellular senescence by evaluating:
- Data integrity
- Sample clustering
- Differential gene expression
- Senescence and proliferation biomarkers

---

## Project Overview

Original study claim:  
> EGCG treatment reverses senescence-associated transcriptional signatures.

Our re-analysis independently verifies this claim using:
- PCA and correlation-based quality control  
- Differential expression analysis using **PyDESeq2**
- Biomarker-level validation (senescence vs proliferative genes)
- Cross-condition contrast testing:  
  - **SEN vs NT**
  - **ST vs SEN**
  - **ST vs NT**

This project focuses on **forensic reproducibility, not biological discovery**.

---

## Dataset

- **Source:** NCBI GEO – GSE286438  
- **Data Type:** Bulk RNA-seq  
- **Conditions:**
  - **NT** – Normal cells  
  - **SEN** – Senescent cells  
  - **ST** – Senescent + EGCG treatment  

## Method
### Sample metadata construction
- Extraction of GSM/SRR mappings from GEO
- Manual verification of NT, SEN, and ST groups
### Quality Control
- Log-normalization
- Pearson correlation matrix
- Principal Component Analysis (PCA)
### Differential Gene Expression
- Implemented using PyDESeq2
- False discovery rate (FDR) correction
- Thresholds:
```
adjusted p < 0.05
|log2FC| ≥ 1
```
### Biomarker Validation
- Senescence markers
- Proliferation-associated genes
- Inflammatory pathway signatures

### Audit Findings
1. EGCG treatment showed incomplete transcriptional reversal of the senescent phenotype.
2. Several canonical senescence markers remained upregulated post-treatment.
3. PCA and correlation analysis revealed partial condition mixing, raising concerns on treatment separability.
>  Full quantitative results and gene lists are presented in the project report.

