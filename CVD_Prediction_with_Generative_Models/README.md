# Data Augmentation Alters Feature Importance in XGBoost for CVD Prediction

## Project Overview
This repository contains the source code and data for a research project investigating the impact of data augmentation on the performance and interpretability of an XGBoost model for Cardiovascular Disease (CVD) prediction. The study compares a baseline model trained on original data against models augmented with the Synthetic Minority Over-sampling Technique (SMOTE) and a Wasserstein Generative Adversarial Network with Gradient Penalty (WGAN-GP). A primary focus is to analyze how these techniques alter the feature importance hierarchy of the final predictive model.

## Folder Structure
The repository is organized into three main directories to maintain a clear and logical project structure:

- **`data/`**: This directory stores the datasets used in the study.
  - `JM.xlsx`: The primary dataset for this research, derived from the "Cardiovascular Disease Dataset" originally sourced from [Mendeley Data](https://data.mendeley.com/datasets/dzz48mvjht/1). The file provided here is a pre-processed version, reduced from its original 1000 entries to 766 by removing invalid and missing values as per the study's data cleaning protocol.

- **`modeling/`**: This folder contains all the Python scripts that implement the research methodology, including data processing, model training, and analysis.

- **`output/`**: An empty directory designated for storing all generated figures, plots, and other visual outputs produced by the scripts in the `modeling/` folder.

## Code Files Description
The core analysis is implemented through a series of scripts, each dedicated to a specific part of the research pipeline. The scripts are numbered to suggest a logical execution order.

1.  `plot_original_data_distribution.py`: A script for generating visualizations to illustrate the distribution and characteristics of the original, pre-processed dataset.
2.  `data_split_and_partitioning.py`: Handles the partitioning of the cleaned dataset into a development set and a final, independent hold-out test set using a stratified sampling strategy.
3.  `baseline_model_training.py`: Establishes the performance benchmark by training and evaluating an XGBoost model exclusively on the original development set without any data augmentation.
4.  `smote_xgboost_nested_cv.py`: Implements a dynamic, nested cross-validation framework for an XGBoost classifier, integrating data augmentation using the Synthetic Minority Over-sampling Technique (SMOTE).
5.  `wgan_gp_xgboost_nested_cv.py`: Contains the implementation of a Wasserstein Generative Adversarial Network with Gradient Penalty (WGAN-GP) for dynamic sample augmentation, integrated into a nested cross-validation framework for the XGBoost classifier.
6.  `feature_importance_analysis.py`: A script designed to conduct a comparative analysis of the "Gain" feature importance metric across the three trained models (Baseline, SMOTE, and WGAN-GP).
7.  `model_performance_comparison_plots.py`: Generates comparative plots, such as radar charts and heatmaps, to visually summarize and compare the final performance metrics of the three distinct models.

## Reproducibility
To replicate the research findings, first ensure you have the required Python environment by installing the dependencies listed in `environment.yml`.
```bash
conda env create -f environment.yml
conda activate your_env_name