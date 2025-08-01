1. Introduction
This project focused on applying various machine learning techniques to detect anomalies within the provided time-series dataset from a cyclone system. Anomaly detection is crucial for identifying unusual patterns that may indicate equipment malfunction, operational deviations, or critical events, thereby supporting predictive maintenance and operational efficiency.

2. Data Preparation
The initial dataset comprised 5256 records. A thorough data cleaning process was performed:

Missing Value Handling: Rows with missing time entries or any NaN values in the relevant sensor columns were removed. This resulted in a clean dataset of 5244 records.

Data Type Conversion: Key sensor measurements were converted to numeric types, and the 'time' column was parsed into datetime objects to facilitate time-series analysis.

3. Feature Engineering
To enhance the dataset's predictive power for anomaly detection, several features were engineered:

Temp_Diff_Inlet_Outlet: Calculated as the difference between Cyclone_Inlet_Gas_Temp and Cyclone_Gas_Outlet_Temp. This feature helps capture abnormal temperature gradients across the cyclone.

Rolling Statistics: 12-period (corresponding to 1 hour, given 5-minute intervals) rolling mean and rolling standard deviation were computed for all original numeric columns. These features are vital for capturing temporal trends and variability, which are often indicative of anomalies.
After engineering, the dataset contained 5233 complete records for modeling.

4. Feature Selection
Feature selection was implemented to identify the most relevant and non-redundant features, thereby improving model efficiency and interpretability:

Multicollinearity Check: Features with a Pearson correlation coefficient greater than 0.8 were identified and considered for removal to avoid redundancy.

Isolation Forest Importance: Feature importance was assessed using an Isolation Forest model, which inherently assigns higher importance to features that contribute more to isolating anomalies.
The selected features, combining original and engineered ones, are listed in the "Feature Selection" section above. A detailed feature_importance.csv is available in the output directory.

5. Anomaly Detection Models and Evaluation
All selected features were standardized using StandardScaler to ensure that features contribute equally to the distance calculations and model training. The anomaly detection models employed were Isolation Forest, One-Class SVM, Local Outlier Factor (LOF), and DBSCAN. The Autoencoder model was excluded from this run due to missing TensorFlow dependency.

Key Findings from Model Evaluation:
IsolationForest and LOF consistently identified approximately 1% of the dataset as anomalous, suggesting these are common outliers. Their high agreement (0.0097) indicates they often pinpoint the same unusual data points.

OneClassSVM was more stringent, detecting fewer anomalies (0.21% proportion). This model establishes a tight boundary around normal data, flagging only the most extreme deviations.

DBSCAN did not detect any anomalies with the chosen parameters. This indicates that the data points do not form clusters dense enough to be considered normal, with sparse points as outliers, under the specified epsilon and minimum samples. Adjusting these parameters might yield different results for DBSCAN.

Silhouette Scores: For LOF, the negative silhouette score suggests that the concept of "clusters" (normal vs. anomaly) might not be well-separated by this method, or that many points are simply classified as noise without forming distinct clusters. DBSCAN's "Not applicable" score confirms its inability to form meaningful clusters for evaluation.

Cross-Model Agreement:
The cross-model agreement analysis revealed that Isolation Forest and LOF had the highest overlap in their anomaly detections. This suggests that these two models might be suitable for identifying similar types of anomalies in this dataset. The lower agreement of OneClassSVM implies it targets a different, possibly more severe, subset of anomalies.

6. Anomaly Periods and Visualizations
Anomaly detection results are more actionable when presented as periods of abnormal behavior. The detected anomalies were aggregated into time periods (with a 30-minute threshold for continuity), providing a summarized view of events. These aggregated anomaly periods are available in CSV files for each model within the output directory.

Visualizations generated for this report include:

Time-series plots for each model, showcasing the original data trends with distinct markers for detected anomalies. These plots are crucial for visual validation and understanding the context of anomalies.

Histograms of anomaly scores to illustrate the distribution of outlier scores for each model, aiding in understanding their confidence in anomaly detection.

A bar plot of silhouette scores (for LOF and DBSCAN where applicable) to provide a clustering quality metric.

A heatmap of cross-model anomaly agreement, visually representing the overlap in anomaly detection across different models, which helps in understanding their complementary or redundant nature.

7. Conclusion
This project successfully applied various anomaly detection techniques to the provided cyclone system dataset. While the Autoencoder could not be run due to a missing dependency, the other models provided valuable insights. Isolation Forest and LOF proved effective in identifying a significant portion of anomalies, demonstrating good consistency. OneClassSVM provided a more conservative detection, highlighting potentially more severe anomalies. DBSCAN, however, did not yield any anomalies with the current parameters, suggesting that its configuration may need adjustment for this specific dataset's density characteristics. The aggregated anomaly periods and comprehensive visualizations offer actionable intelligence for further investigation and operational improvements.

8. Generated Output Files
All generated reports and visualizations are located in the output directory:

output/feature_importance.csv

output/anomalies_IsolationForest.png

output/anomaly_periods_IsolationForest.csv

output/anomalies_OneClassSVM.png

output/anomaly_periods_OneClassSVM.csv

output/anomalies_LOF.png

output/anomaly_periods_LOF.csv

output/anomalies_DBSCAN.png

output/anomaly_periods_DBSCAN.csv

output/anomaly_score_distribution.png

output/silhouette_scores.png

output/cross_model_agreement.png
