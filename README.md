# Cyclone Preheater Anomaly Detection

This repository contains the code and presentation for anomaly detection on the cyclone preheater dataset, submitted by Rahul Rai.

## Project Overview
- **Dataset**: `/content/data (5) (1) (1) (1) (1)(internship-data-1).csv` (370k records, sampled to 10,000 rows).
- **Task**: Unsupervised anomaly detection using Isolation Forest, One-Class SVM, LOF, DBSCAN, and Autoencoder.
- **Features**: 6 numerical variables, with engineered features (temperature difference, rolling mean/std).
- **Evaluation**: Silhouette scores, anomaly score distributions, cross-model agreement.
- **Outputs**: Anomaly periods (CSV), time-series plots, evaluation plots (anomaly score distribution, silhouette scores, cross-model agreement).

## Repository Structure
- `anomaly_detection_pipeline_updated.py`: Main script for data preparation, model checking, and visualization.
- `data_preparation_and_model_checking_presentation_updated.tex`: 4-slide LaTeX presentation summarizing data preparation and model checking.
- `requirements.txt`: Python dependencies.
- `output/`: Directory for generated files (e.g., `feature_importance.csv`, `anomaly_periods_*.csv`, `anomalies_*.png`, `anomaly_score_distribution.png`).
- `.gitignore`: Excludes generated files and Python cache.

## Setup Instructions
1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
Place Dataset:

Ensure the dataset is at /content/data (5) (1) (1) (1) (1)(internship-data-1).csv (e.g., in Google Colab) or adjust the path in the script.


Run Script:
bashpython anomaly_detection_pipeline_updated.py

Compile Presentation:
bashpdflatex data_preparation_and_model_checking_presentation_updated.tex

Ensure output/anomaly_score_distribution.png is in the output directory.



Generated Outputs

feature_importance.csv: Feature importance from Isolation Forest.
anomaly_periods_<model>.csv: Anomaly periods for each model.
anomalies_<model>.png: Time-series plots of anomalies.
anomaly_score_distribution.png: Histogram of anomaly scores.
silhouette_scores.png: Bar plot of silhouette scores for LOF and DBSCAN.
cross_model_agreement.png: Heatmap of cross-model anomaly agreement.

Submission
Zip the Rahul_Rai folder containing all files and outputs for submission:
bashzip -r Rahul_Rai.zip Rahul_Rai#   c y c l o n e _ - p r e h e a t e r _ a n a m o l y  
 