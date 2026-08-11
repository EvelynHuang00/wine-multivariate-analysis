# Multivariate Analysis of Wine Physicochemical Structure

How do the physicochemical profiles of red and white wines differ, and what multivariate patterns are associated with wine quality?

This project analyzes the physicochemical structure of Portuguese Vinho Verde wines using correlation analysis and principal component analysis (PCA). The goal is to identify dominant patterns of covariation among chemical measurements, examine how red and white wines differ in a low-dimensional representation, and explore how wine quality varies along these multivariate directions.

## Overview

The analysis addresses three main questions:

1. Do red and white wines occupy distinct regions in a low-dimensional physicochemical space?
2. What are the strongest dependence structures among the measured chemical properties?
3. Which combinations of physicochemical variables explain the dominant variation in the data, and how does wine quality vary along these directions?

## Data

The dataset contains **6,497 Portuguese Vinho Verde wines**, including:

- 1,599 red wines
- 4,898 white wines
- 11 continuous physicochemical measurements
- A sensory quality score on a 0–10 scale

After removing 1,177 duplicate records, the final analysis contains **5,320 unique observations**.

The dataset is publicly available through the UCI Machine Learning Repository.

## Methods

### Exploratory Data Analysis

I examined the distributions and scales of the physicochemical variables before applying multivariate methods.

Several variables, including residual sugar, chlorides, and sulfur dioxide measures, showed substantial skewness and extreme observations. Predictors were therefore standardized before PCA so that variables measured on larger scales would not dominate the analysis.

### Correlation Analysis

Correlation matrices were examined for the full dataset and separately for red and white wines.

Several strong dependence patterns emerged:

- Free and total sulfur dioxide form a strong correlated pair.
- Residual sugar is positively associated with density and sulfur dioxide.
- Alcohol and density show a strong negative relationship.
- Some relationships differ substantially between red and white wines.

Quality is most positively associated with alcohol and negatively associated with density and volatile acidity in the pooled data.

### Principal Component Analysis

PCA was applied to the standardized physicochemical predictors.

The first two principal components explain approximately **49.7% of total standardized variance**:

- **PC1:** 27.2%
- **PC2:** 22.5%

The first three components satisfy the Kaiser criterion, but interpretation focuses on PC1 and PC2 because they capture the dominant and most interpretable structure.

I interpret the two leading components as:

- **PC1 — Production Style & Preservation Axis**  
  Primarily contrasts higher residual sugar and sulfur dioxide with higher chloride levels.

- **PC2 — Fermentation & Body Axis**  
  Primarily reflects the contrast between density and alcohol.

## Key Results

### Red and white wines show clear multivariate separation

Red and white wines separate strongly along PC1.

White wines tend to occupy the direction associated with higher residual sugar and sulfur dioxide, while red wines are concentrated toward the opposite side of the component.

### Quality varies primarily within wine type

The dominant red–white separation occurs along PC1, but quality differences appear more strongly along PC2.

Higher-quality wines occur more frequently toward the region associated with:

- higher alcohol
- lower density

This suggests that wine type and wine quality are associated with different directions of multivariate variation.

### Correlation structure helps explain the PCA representation

The PCA directions reflect several relationships already visible in the correlation analysis, particularly:

- sulfur dioxide dependence
- the residual sugar–density relationship
- the alcohol–density tradeoff

The results therefore provide a compact low-dimensional representation of the major physicochemical relationships in the dataset.

## Main Takeaways

- Red and white wines have clearly different multivariate physicochemical profiles.
- The dominant separation between wine types is associated with residual sugar, sulfur dioxide, and chloride levels.
- A second major direction captures an alcohol–density tradeoff within both wine types.
- Wine quality varies more clearly along this within-type alcohol–density direction than along the primary red–white separation.
- PCA provides an interpretable summary of the main chemical dependence structure, but the results should be viewed as descriptive rather than causal.

## Repository Structure

```text
wine-multivariate-analysis/
│
├── README.md
├── report.pdf
│
├── data/
│   └── README.md
│
├── notebooks/
│   └── wine_analysis.ipynb
│
└── figures/
    ├── feature_distributions.png
    ├── correlation_heatmaps.png
    ├── pca_scree_plot.png
    ├── pca_scores.png
    └── pca_loadings.png
