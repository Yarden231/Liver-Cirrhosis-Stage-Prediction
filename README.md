# Liver Cirrhosis Stage Prediction

## Repository Structure
```
.
├── cirrhosis.csv                # Original dataset file
├── cirrhosis_preprocessed.csv   # Cleaned and preprocessed dataset
├── EDA.ipynb                    # Exploratory Data Analysis notebook
├── Models.ipynb                 # Model implementation and evaluation
└── Pre-Processing.ipynb         # Data preprocessing steps
```

## Overview
This project uses machine learning techniques to predict the stage of liver cirrhosis based on patient clinical data. The goal is to develop accurate models that can classify patients into different cirrhosis stages, which can aid in early detection and treatment planning.

## Background
Cirrhosis is a serious liver condition characterized by the replacement of healthy liver tissue with scar tissue, leading to progressive liver dysfunction. It is the 12th leading cause of death in the United States. Early diagnosis is crucial for effective treatment, but the disease often remains asymptomatic in its early stages.

## Dataset
The project uses the Cirrhosis Prediction Dataset from the Mayo Clinic study on primary biliary cirrhosis (1974-1984), available from the UC Irvine Machine Learning Repository. The dataset includes:
- 418 patient records
- 19 explanatory variables (biochemical markers, clinical indicators, demographic data)
- Target variable: Histologic stage of disease (1-4)

Key features include:
- Demographic data (Age, Sex)
- Clinical indicators (Ascites, Hepatomegaly, Spiders, Edema)
- Biochemical markers (Bilirubin, Cholesterol, Albumin, Copper, Alkaline Phosphatase, SGOT, Triglycerides, Platelets, Prothrombin time)
- Treatment information (Drug type, survival days)

## Methodology

### Data Preparation
1. **Cleaning**: Removed ID column and handled missing values using median imputation
2. **Target Variable Adjustment**: Merged stages 1 and 2 due to low sample sizes
3. **Outlier Handling**: Applied logarithmic transformation to variables with extreme values
4. **Feature Engineering**: Discretized continuous variables using quantile-based binning
5. **Encoding**: Applied one-hot encoding for multi-class categorical features and label encoding for binary features
6. **Feature Selection**: Used Variance Inflation Factor analysis to identify and remove features with high multicollinearity
7. **Scaling**: Applied both standardization and min-max scaling for model evaluation

### Models Evaluated
- Random Forest
- XGBoost
- CatBoost
- Artificial Neural Network (ANN)
- LightGBM
- K-Nearest Neighbors (KNN)

### Hyperparameter Tuning
Used Optuna framework for efficient hyperparameter optimization, focusing on maximizing F1-score.

## Results
- Random Forest achieved the best overall performance with 72% accuracy and a weighted F1-score of 0.72
- The models generally showed increasing recall with disease severity, making them more reliable for detecting advanced stages
- Feature importance analysis identified Triglycerides and Cholesterol as the strongest predictors, followed by Copper concentration and N_Days

## Key Findings
1. Gradient boosting algorithms (Random Forest, LightGBM, CatBoost) performed best for this task
2. Classification accuracy increased with disease severity, a clinically valuable characteristic
3. Blood lipid indicators (Triglycerides, Cholesterol) were the most influential predictors
4. The limited dataset size (412 samples after cleaning) presented challenges for model training

## Implementation Details

The project is organized into three main Jupyter notebooks:

### 1. EDA.ipynb
- Detailed exploratory data analysis
- Statistical summaries of variables
- Correlation analysis and visualization
- Investigation of relationships between features and target variable
- Identification of data quality issues

### 2. Pre-Processing.ipynb
- Data cleaning and handling of missing values
- Feature engineering and transformation
- Discretization of continuous variables
- Categorical variable encoding
- Feature selection and scaling

### 3. Models.ipynb
- Implementation of various machine learning models
- Hyperparameter tuning using Optuna
- Model evaluation and comparison
- Feature importance analysis
- Visualization of model performance

## Contributors
- Sivan Raviv
- Avital Finanser
- Yarden Choen

## Acknowledgments
This project was completed as part of the Machine Learning and Data Mining course (364-2-5091) at Ben Gurion University of the Negev, under the guidance of Prof. Boaz Lerner.
