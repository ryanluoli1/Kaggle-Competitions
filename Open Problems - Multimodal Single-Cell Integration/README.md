# Open Problems - Multimodal Single-Cell Integration
Link: https://www.kaggle.com/competitions/open-problems-multimodal

## Achievements:
1. Silver Medal 
2. Top 4%

## Introduction:
- The goal of this competition is to **predict how DNA, RNA, and protein measurements co-vary in single cells** as bone marrow stem cells develop into more mature blood cells.
- The **chromatin accessibility** (DNA), **gene expression** (RNA) and **protein levels** are the **single-cell modalities** measured and to be predicted.

## Data and Tasks
- The datasets consist of the **modalities measurements of cells** donated by **four healthy human** which were measured using **two different test kits** (CITEseq and Multiome) at **five time points** (day 2,3,4,7,10):
    - the **Multiome kit** measures **chromatin accessibility** (DNA) and gene expression (**RNA**)
    - the **CITEseq kit** measures gene expression (**RNA**) and **surface protein levels**
- Following the central dogma of molecular biology (**DNA->RNA->Protein**), the tasks of this competition are:
    - for the **Multiome** samples: given chromatin accessibility, **predict RNA**
    - for the **CITEseq** samples: given RNA, **predict protein levels**

##
