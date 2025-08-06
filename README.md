# preeclampsia-risk-prediction

This script implements a machine learning pipeline for predicting **pre-eclampsia (PE)** using gene expression data. It includes functionality for preprocessing gene expression matrix series files, applying various machine learning classifiers, performing feature selection, and evaluating model performance using clinical metrics such as accuracy, precision, sensitivity, specificity, F1-score, and AUC.

---

## Requirements

To run this code, you will need to install the following Python libraries:

### Python Packages:

- **pandas**: For data manipulation and analysis.
- **numpy**: For numerical operations.
- **scikit-learn**: For machine learning algorithms, preprocessing, model evaluation, and feature selection.
- **xgboost**: For XGBoost classifier and model training.
- **matplotlib**: For plotting graphs and visualizations.
- **seaborn**: For statistical data visualization.
- **tqdm**: For displaying progress bars in loops.
- **torch**: For deep learning models using PyTorch.
- **shap**: For model interpretation and SHAP values.
- **statistics**: For basic statistical operations like mean calculation.
- **time**: For tracking runtime and performance.
- **gzip**: For reading compressed gene expression files.

---

## Installation Instructions

You can install the required Python libraries using pip. Use the following command:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn tqdm torch shap
```bash

# RNA-seq Count Data Processing from GEO (GSE114691)

This R script downloads raw RNA-seq count data from the GEO database, performs basic filtering and transformation, and optionally exports the processed data.

## Requirements

- R (version >= 3.5)
- `data.table` package

Install the required package with:

```r
install.packages("data.table")
```

## Usage

1. **Load count data from GEO:**

```r
urld <- "https://www.ncbi.nlm.nih.gov/geo/download/?format=file&type=rnaseq_counts"
path <- paste(urld, "acc=GSE114691", "file=GSE114691_raw_counts_GRCh38.p13_NCBI.tsv.gz", sep="&")
tbl <- as.matrix(data.table::fread(path, header=TRUE, colClasses="integer"), rownames=1)
```

2. **Pre-filter low count genes:**

```r
# Keep genes with counts >= 10 in at least 2 samples
keep <- rowSums(tbl >= 10) >= 2
tbl <- tbl[keep, ]
```

3. **Log-transform the counts:**

```r
dat <- log10(tbl + 1)
```

*Note:* You can use variance stabilizing transformation (`vst`) from `DESeq2` as an alternative.

4. **Export processed data (optional):**

```r
write.csv(dat, file = "processed_expression.csv")
```

## Description

- The script downloads raw gene expression counts for dataset GSE114691.
- Lowly expressed genes are filtered out to reduce noise.
- Log-transformation stabilizes variance for downstream analysis.
- The processed matrix can be saved for further use.


