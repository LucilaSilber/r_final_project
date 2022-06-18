---
output:
  html_document: default
  pdf_document: default
---
# SISE2601 Advanced Data Analysis in R : Final Project
================
Team name: T

## Load Packages

Load the following libraries to reproduce the code:
```bash
library(knitr)
library(tidyverse)
library(broom)
library(htmltools)
library(expss)
library(dplyr)
library(haven)
library(ggplot2)
```
## Load Dataset
Data should be stored under the path: "directory/data/"
```bash
X3rd_assessment <- read_sav("data/3rd assessment.sav")
child_risk_t12 <- read_sav("data/child_risk_t12.sav")
```

## Preprocessing
The dataset consists of 3 questionnaires that need to be preprocessed and merged into a unified dataset.

The preprocessing steps are as follows:
* Duplicated IDs were merged into a single entry.
* Null values were replaced with the most frequent value in the relevant columns.
* Originally questionnaires 1 & 2 were merged. The third questionnaire was merged into the data set, using an id-join.

## Analysing the Data

#### Kmeans
A seed set to enable reproduction of code.
The first attempt resulted in 3 clusters, one of which with a single entry. 
The single entity was identified as an outlier, thus removed from the dataset.
The second attempt resulted in 4 valid clusters, of size:
1. 83
2. 74
3. 67
4. 13

The results of the second attempt were analyzed to find the most significant variables. The aim was to identify the difference between clusters in regards to our research question.

Examples of reviewed independent variables:
* Frequency of contact with a mentor
* Feeling of trust towards the stuff in the boarding school.
* Whether the subject is in contact with the stuff in the boarding school since they left.

Examples of reviewed variables:
* Education Level
* Ability to cover monthly expenses.

A link was found between the independent and dependent variables, between the different clusters.

#### Regression

##### Linear Regression
First, A linear regression model was generated based on the significant variables identified by Kmeans. 
A separate model was fit for each dependent variable.
These models resulted in low adjusted R-squared values and low significance level for the coefficients.
Therefore, we continued the analysis with stepwise regression models.

##### Stepwise Regression
Stepwise regression models were fit for significant dependent variables in order to identify the most significant independent variables.
Two additional models were fit for two dependent variables.
Some of the independent variable identified by Kmeans as significant turned out to be significant variable in the stepwise regression models.
