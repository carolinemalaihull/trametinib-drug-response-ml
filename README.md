# Predicting Trametinib Sensitivity Using Cancer Driver Mutations 

A machine learning data preparation and exploratory analysis project integrating genomic mutation data with pharmacological drug response measurements.

## Project Overview

Targeted cancer therapies can produce dramatically different responses between patients, even when tumours arise from the same tissue. One important reason is the underlying genomic landscape of the cancer.

This project investigates whether driver mutations can be integrated with drug response data to support future machine learning models capable of predicting sensitivity to Trametinib, a clinically approved MEK inhibitor.

Using publicly available datasets from the Genomics of Drug Sensitivity in Cancer (GDSC) and Cell Model Passports, mutation profiles were merged with pharmacological response measurements to produce a high-quality dataset suitable for predictive modelling.

This repository focuses on:

Data integration
Data cleaning and preprocessing
Exploratory data analysis (EDA)
Feature preparation for machine learning
Model development 

## Biological Background

Cancer develops through the accumulation of genetic alterations.
Some mutations are driver mutations, meaning they directly contribute to tumour development by altering important signalling pathways.

Trametinib targets the MAPK signalling pathway, making mutations in genes such as:

BRAF
KRAS
NRAS
NF1

particularly relevant when investigating drug sensitivity.

Understanding how these genomic alterations relate to drug response could ultimately support:

Biomarker discovery
Patient stratification
Precision oncology
Personalised medicine

## Objectives

The objectives of this project were to:

Merge genomic mutation and drug response datasets
Clean and validate the integrated dataset
Perform exploratory data analysis
Investigate mutation distributions
Explore relationships between mutation burden and Trametinib response
Produce a machine learning-ready dataset
Datasets
Cell Model Passports

Contains genomic information for hundreds of cancer cell lines including:

Driver mutations
Gene annotations
Mutation effects

https://cellmodelpassports.sanger.ac.uk/

Genomics of Drug Sensitivity in Cancer (GDSC)

Contains drug response measurements across large cancer cell line panels.

Drug response was measured using:

LN(IC50)
Area Under Curve (AUC)

https://www.cancerrxgene.org/

## Technologies Used

Python
pandas
NumPy
matplotlib
seaborn
SciPy
Jupyter Notebook
Project Workflow
Raw GDSC Drug Response
            │
            ▼
Filter Trametinib
            │
            ▼
Load Cell Model Passports Mutations
            │
            ▼
Standardise identifiers
            │
            ▼
Merge datasets
            │
            ▼
Data cleaning
            │
            ▼
Exploratory Data Analysis
            │
            ▼
Machine Learning-ready dataset
Exploratory Analysis

The exploratory analysis included:

Distribution of Trametinib sensitivity
Cancer type composition
Driver mutation frequencies
MAPK pathway mutation burden
Mutation burden versus drug sensitivity
Correlation analysis
Summary statistics
Repository Structure
├── notebooks/
│   └── 01_data_exploration.ipynb
│
├── data/
│   ├── GDSC2_fitted_dose_response_27Oct23.xlsx
│   └── mutations_summary_20260724.csv
│
├── figures/
│
├── README.md
└── requirements.txt

## Running the Notebook

Clone the repository

git clone https://github.com/carolinemalaihull/trametinib-drug-response-ml.git

Install dependencies

pip install -r requirements.txt

Download the public datasets from:

Cell Model Passports
GDSC

Place them inside

data/

Run

notebooks/01_data_exploration.ipynb
Future Work

Future development will include:

Feature engineering
Mutation encoding
Machine learning classification
Regression modelling
Cross-validation
Model interpretation using SHAP values
Biomarker identification
Disclaimer

This repository contains work completed using publicly available datasets for educational and portfolio purposes.

The analyses, code and interpretations are my own and do not represent the views or research programmes of my employer.

No proprietary or confidential data are included.

Author

Caroline Hull, PhD

Associate Director, Translational Oncology
Machine Learning & AI (Master's) Student

Interests

Translational oncology
Cancer immunology
Machine learning
Precision medicine
AI for drug discovery