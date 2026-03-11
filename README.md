# Characterising the Tumour Microenvironment of Responders and Non-Responders to Anti-LAG-3-Based Therapy in Advanced Melanoma.

Full analysis code for the Honours thesis:

<b>"Characterising the Tumour Microenvironment of Responders and Non-Responders to Anti-LAG-3-Based Therapy in Advanced Melanoma"</b> <i>Nabila Zulkapeli</i>

This repository contains scripts and notebooks used to analyse <b>spatial transcriptomics data</b>. The dataset consists of spatial transcriptomics profiles generated using the <b>10x Xenium platform</b> from patient-derived melanoma tissue microarrays constructed from high-tumour and peritumour cores.

The aim of the analysis is to <b>identify tumour microenvironment (TME) features associated with response or resistance to anti-LAG-3-based immunotherapy</b> in advanced melanoma.

## Project Overview

This project investigates spatial and molecular characteristics of the TME in patients treated with anti-LAG-3-based immunotherapy. Samples were stratified into:
- Responders (R)
- Non-responders (NR) <br>

The analysis integrates spatial transcriptomics, compositional analysis, differential expression, pathway enrichment, and cell–cell communication inference to identify spatiomolecular features associated with treatment response/resistance.

<img width="2140" height="1629" alt="new study overview" src="https://github.com/user-attachments/assets/29c53db1-03f0-4e01-8877-526d47c34bc6" /> <br>

All analyses in this repository were used to generate the figures and results presented in the thesis.

## Key Methods
- Spatial transcriptomics analysis
- Compositional cell type analysis (scCODA)
- Differential gene expression (PyDESeq2)
- Gene set enrichment analysis (fgsea)
- Spatial neighbourhood analysis
- Cell–cell communication inference (CellPhoneDB, LIANA)

## Repository Structure

### Data Preprocessing
`filter_adata.py`

Merges AnnData with clinical metadata and performs quality control filtering, including:
- Removal of tumour cores with low melanoma cell counts
- Removal of cores with low total cell counts
- Exclusion of high tumour-infiltrating lymphocyte (TIL) cores
- Additional filtering steps to improve downstream analysis

### Exploratory Analysis
`ICI_intro_stats_trials.ipynb`

Exploratory analysis of clinical trial outcomes:
- summarises descriptive statistics from
  - CheckMate-067
  - RELATIVITY-047
- visualises treatment response and toxicity for:
  - first-line therapy (anti-CTLA-4 + anti-PD-1)
  - second-line therapy (anti-LAG-3 + anti-PD-1)

### Dimensionality Reduction & Visualisation
`umap_matrixplot.ipynb`

<img width="2149" height="788" alt="image" src="https://github.com/user-attachments/assets/ae45f39f-5214-4e42-8ea1-a134a846835e" />
- Generates UMAP embeddings to visualise cell type distribution
- Produces matrix plots showing mean gene expression across cell populations

### Cell Type Composition Analysis
`sccoda_ctp.ipynb`
- Compares cell type proportions between responders and non-responders using <B>scCODA (v0.1.9)</B>, a Bayesian framework designed for compositional single-cell data.

### Differential Gene Expression
`pertpy_deg.ipynb`
- Performs differential gene expression analysis in R versus NR using <b>pyDESeq2 (v0.5.3)</b>

### Gene Set Enrichment Analysis
`fgsea_region.R`
- Runs pathway enrichment separately in <b>peritumour</b> and <b>high-tumour</b> tissue cores using <b>fgsea (v1.32.4)</b>

`fgsea_figs.ipynb`

<img width="2103" height="877" alt="image" src="https://github.com/user-attachments/assets/f6b5c3c2-d277-4972-bda5-544809d1b930" />
- Generates visualisations used to present gene set enrichment results

### Neighbourhood and Spatial Niche Analysis
`nhood_niche.ipynb`

Performs spatial neighbourhood enrichment analysis across tumour cores and response groups.
Key steps include:
- clustering cellular neighbourhoods
- extracting flat clusters from dendrograms
- identifying distinct spatial niches associated with responders and non-responders

### Cell-Cell Communication Analysis
`liana_ccc.ipynb` <br>
- Infers ligand-receptor interactions in spatial niches using:
  - <b>CellPhoneDB (v2)</b>
  - <b>LIANA v1.6.1</b><br>
This analysis explores potential cell-cell interactions between cell populations associated with treatment response.

### Figure Generation
Plots were generated in Python and exported as vector PDFs for editing in <b>Adobe Illustrator</b>. 
These parameters were used to ensure .pdf files had editable text and vectors:<br>
1. plt.rcParams['pdf.fonttype'] = 42<br>
2. plt.rcParams['ps.fonttype'] = 42<br>

Post-processing included:
- assembling multi-panel figures
- adjusting colours when not data-relevant (e.g., bar plots)
- improving readability for publication-quality figures

## Tools & Libraries

### Python 
- scanpy / AnnData
- scCODA
- PyDESeq2
- LIANA
- CellPhoneDB
- matplotlib
- seaborn

### R
- fgsea

## Reproducibility
This repository documents the full analysis workflow from data preprocessing through statistical analysis and visualisation.

Due to patient data restrictions, raw spatial transcriptomics datasets are not included in this repository. However, the scripts and notebooks provide a complete record of the analysis pipeline used in this project.
