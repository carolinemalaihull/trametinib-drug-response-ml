# Predicting Trametinib Sensitivity from Cancer Driver Mutations

## Overview

This project explores whether cancer driver mutation profiles can be used to predict the response of cancer cell lines to Trametinib using machine learning.

Trametinib is a targeted inhibitor of MEK1 and MEK2, key components of the RAS–RAF–MEK–ERK (MAPK) signalling pathway. Dysregulation of this pathway is common across multiple cancer types and can occur through genomic alterations affecting genes including KRAS, NRAS, BRAF, NF1, and other pathway-associated genes.

Using publicly available pharmacogenomic data, this project investigates whether genomic features of cancer cell lines are associated with differential sensitivity to Trametinib and whether these features can be used to build predictive machine learning models.

## Research Question

**Can cancer driver mutation profiles predict cancer cell line sensitivity to Trametinib?**

A secondary biological question is:

**Which genomic alterations are most strongly associated with predicted sensitivity or resistance to Trametinib?**

## Biological Background

The MAPK signalling pathway plays an important role in regulating cell proliferation, differentiation, and survival.

A simplified representation of the pathway is:

Receptor Tyrosine Kinase (RTK)

↓

RAS (KRAS / NRAS / HRAS)

↓

RAF (e.g. BRAF)

↓

MEK1 / MEK2

↓

ERK1 / ERK2

↓

Cell proliferation and survival

Trametinib inhibits MEK1 and MEK2, reducing downstream MAPK signalling.

Genomic alterations affecting this pathway may influence how dependent a cancer cell is on MAPK signalling and therefore potentially affect its response to MEK inhibition. However, the relationship between individual mutations and drug response is complex and may depend on additional genomic alterations and tumour lineage.

This project uses machine learning to investigate these relationships rather than assuming that the presence of a specific mutation necessarily causes sensitivity or resistance.

## Data Sources

### Genomics of Drug Sensitivity in Cancer (GDSC)

Drug-response measurements are obtained from the Genomics of Drug Sensitivity in Cancer (GDSC) resource.

The dataset contains experimental measurements of cancer cell line responses to anti-cancer compounds.

For this project, the analysis is restricted to cancer cell lines treated with **Trametinib**.

The primary drug-response variable is:

- `LN_IC50` — the natural logarithm of the half-maximal inhibitory concentration (IC50).

Lower IC50 values generally indicate that a lower concentration of drug is required to inhibit cell growth, consistent with greater drug sensitivity.

### Cell Model Passports

Cancer driver mutation data are obtained from the Cell Model Passports resource.

The mutation dataset contains genomic alterations identified across cancer cell models, including:

- Gene
- Protein mutation
- Mutation effect
- Variant allele frequency (VAF)
- Cancer driver annotation

Cell models are linked between the mutation and drug-response datasets using the Sanger Model ID.

## Dataset Overview

The GDSC drug-response dataset contains:

- 242,036 drug–cell line response observations
- Multiple anti-cancer compounds
- Drug targets and associated pathways
- Experimental response measurements including `LN_IC50` and AUC

For Trametinib specifically:

- 966 unique cancer cell lines have drug-response measurements
- 948 of these cell lines also have corresponding records in the driver mutation dataset
- Mutation-data coverage is approximately 98.1%

This provides a dataset in which experimentally measured Trametinib response can be integrated with genomic information.

## Planned Features

The initial analysis will investigate driver mutations affecting the MAPK pathway and related cancer signalling pathways.

Candidate genomic features include:

- BRAF
- KRAS
- NRAS
- HRAS
- NF1
- MAP2K1
- MAP2K2
- EGFR
- ERBB2
- PIK3CA
- PTEN
- TP53

Mutation information will be transformed into model-level features suitable for machine learning.

Cancer type may also be included as a feature to account for differences in drug response associated with tumour lineage.

## Target Variable

The initial machine learning task will be formulated as a **regression problem**.

**Target:**

`LN_IC50`

The objective is to predict experimentally measured Trametinib response from genomic characteristics of each cancer cell line.

A future extension may investigate classification of cell lines into sensitive and resistant groups, provided that a biologically and statistically justified threshold can be defined.

## Project Workflow

The planned workflow is:

1. Data acquisition and validation
2. Exploratory data analysis
3. Integration of GDSC drug-response and Cell Model Passports mutation data
4. Genomic feature engineering
5. Data preprocessing
6. Exploratory analysis of mutation–response relationships
7. Machine learning model development
8. Model evaluation and comparison
9. Feature importance and model interpretation
10. Biological interpretation of potential sensitivity and resistance markers

## Planned Machine Learning Models

Initial models may include:

- Linear Regression / Regularised Regression
- Random Forest Regression
- Gradient Boosting / XGBoost

Model performance will be evaluated using appropriate regression metrics, potentially including:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R²

Cross-validation will be used where appropriate to estimate model generalisation performance.

## Model Interpretation

An important objective of this project is not only to predict drug response but also to investigate which genomic features contribute to model predictions.

Potential approaches include:

- Feature importance
- Permutation importance
- SHAP values

This may help identify genomic alterations associated with predicted Trametinib sensitivity or resistance.

These associations will be interpreted as exploratory and hypothesis-generating rather than evidence of causal biological relationships.

## Limitations

Several limitations should be considered:

- Cancer cell lines are experimental models and do not fully represent patient tumours.
- Mutation status alone may not capture all mechanisms influencing drug response.
- Gene expression, copy-number variation, epigenetic state, and protein activity may also influence Trametinib sensitivity.
- Associations identified by machine learning do not establish causality.
- Findings from computational analysis would require experimental and clinical validation.

## Future Work

Future extensions could incorporate additional molecular data, including:

- Gene expression
- Copy-number alterations
- Proteomic data
- Additional cancer driver mutations

The project could also be expanded to compare responses across multiple MEK inhibitors or investigate whether models trained on one compound generalise to other drugs targeting the same pathway.

## Project Status

**In progress**

Current progress:

- [x] GDSC drug-response data acquired
- [x] Cancer driver mutation data acquired
- [x] Data sources linked using Sanger Model IDs
- [x] Trametinib selected as the initial compound
- [x] Drug-response and mutation-data overlap assessed
- [ ] Exploratory data analysis
- [ ] Mutation feature engineering
- [ ] Final dataset construction
- [ ] Machine learning modelling
- [ ] Model interpretation
- [ ] Biological interpretation

## Disclaimer

This project is an independent educational and portfolio project using publicly available research data. It is intended to explore applications of machine learning in pharmacogenomics and drug-response prediction and is not intended for clinical decision-making. It does not contain confidential information and does not represent the views, research or intellectual property of my employer.

