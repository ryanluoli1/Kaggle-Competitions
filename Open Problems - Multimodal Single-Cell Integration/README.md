# Open Problems - Multimodal Single-Cell Integration

Link: https://www.kaggle.com/competitions/open-problems-multimodal


## Achievements:

1. Silver Medal 
2. Top 4%


## Introduction:

The goal of this competition is to **predict how DNA, RNA, and protein measurements co-vary in single cells** as bone marrow stem cells develop into more mature blood cells. The **chromatin accessibility** (DNA), **gene expression** (RNA) and **protein levels** are the **single-cell modalities** measured and to be predicted.


## Data

- The datasets consist of the **modalities measurements of cells** donated by **four healthy human** which were measured using **two different test kits** (CITEseq and Multiome) at **five time points** (day 2,3,4,7,10):
    - the **Multiome kit** measures **chromatin accessibility** (DNA) and gene expression (**RNA**)
    - the **CITEseq kit** measures gene expression (**RNA**) and **surface protein levels**

- The split between **training** and **test** (public and private) sets:
<img src="https://github.com/ryanluoli1/Kaggle-Competitions/blob/main/Open%20Problems%20-%20Multimodal%20Single-Cell%20Integration/Images/1.png" alt="Alt text" width="600"/>

- **`Training set`**:
    - cells from donors 13176, 31800 and 32606
    - CITEseq samples from day 2, 3 and 4
    - Multiome samples from day 2, 3, 4 and 7
 
- **`Test set (Public)`**:
    - cells from donor 27678 only (evaluating the models' performance on a new donor)
    - CITEseq samples from day 2, 3 and 4
    - Multiome samples from day 2, 3 and 7
    
- **`Test set (Private)`**:
    - cells from all 4 donors
    - CITEseq samples from only day 7
    - Multiome samples from only day 10
    - evaluating the models' performance on a new time point


## Tasks

- Following the central dogma of molecular biology (**DNA->RNA->Protein**), the tasks of this competition are:
    - for the **Multiome** samples: given chromatin accessibility, **predict RNA**
    - for the **CITEseq** samples: given RNA, **predict protein levels**

- This is a typical **multiple output regression** problem


## Tasks Breakdown

- **`Task 1: (CITEseq)`**
    - **Inputs**: 
        - 70988×22050: 70988 cells, each has 22050 features (gene expressions)
        - high dimensional sparse matrix
        - we will apply library-size normalization and log1p transformation to the input data
    - **Outputs**:
        - 70988×140: 70988 cells, 140 protein levels
        
- **`Task 2: (Multiome)`**
    - **Inputs**: 
        - 105942×22894: 105942 cells, each has 228942 features (chromatin accessibility)
        - dense matrix, large p samll n
        - we will apply log(TF)×log(IDF) to make the input data continuous
    - **Outputs**:
        - 105942×23418: 105942 cells, 23418 gene expressions     
        
        
 ## Evaluation Metric
 
 - Predictions are ranked using the **`Pearson correlation coefficient`**
 - The overall score is the **average** of each sample's correlation score.
 - If a sample's predictions are **all the same**, that sample is **scored as -1.0**
<img src="https://github.com/ryanluoli1/Kaggle-Competitions/blob/main/Open%20Problems%20-%20Multimodal%20Single-Cell%20Integration/Images/2.png" alt="Alt text" width="500"/>
 
 
