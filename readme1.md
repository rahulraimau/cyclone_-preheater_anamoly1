# 🚨 Cyclone Sensor Anomaly Detection Project

This project performs **anomaly detection** on a large-scale industrial sensor dataset (400,000+ rows) collected from a cyclone system. Using time-series and statistical models, the pipeline identifies abnormal behavior based on six core sensor readings.

---

## 📁 Dataset

**Source:** Internal Internship Dataset  
**Rows:** 400,000+  
**Features:**
- `Cyclone_Inlet_Gas_Temp`
- `Cyclone_Material_Temp`
- `Cyclone_Outlet_Gas_draft`
- `Cyclone_cone_draft`
- `Cyclone_Gas_Outlet_Temp`
- `Cyclone_Inlet_Draft`

---

## 🔍 Project Goals

- Clean and preprocess high-frequency sensor data.
- Explore feature trends, correlations, and seasonal behavior.
- Detect anomalies using:
  - Z-Score Method
  - Isolation Forest
  - One-Class SVM
  - Elliptic Envelope
- Visualize and export anomaly results for further analysis.

---

## 🛠️ Tools & Libraries

- Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)
- FPDF (for generating PDF reports)
- Plotly Express (interactive visualization)
- Jupyter / Google Colab for experimentation

---

## 📊 Exploratory Data Analysis

- Feature summary with mean, std, min, max.
- Correlation heatmap for variable inter-dependencies.
- Line plots of sensor values over time.
- Overlay of detected anomalies on sensor plots.

---

## 📌 Results

- Generated anomaly flags using four different techniques.
- Saved as `.csv` for post-analysis.
- Created `.png` plots highlighting anomalies.
- PDF report summarizes methodology and findings.

📂 Output Files:
├── feature_summary_cleaned.csv
├── anomalies_cleaned.csv
├── Cyclone_Sensor_Anomaly_Report.pdf
├── Cyclone_<FeatureName>_anomalies.png
├── correlation_heatmap.png

yaml
Copy
Edit

---

## 📦 How to Use

1. Clone the repo:
   ```bash
   git clone https://github.com/<your-username>/cyclone-anomaly-detection.git
   cd cyclone-anomaly-detection
Install requirements:

bash
Copy
Edit
pip install -r requirements.txt
Run the notebook or script to analyze new data.

📘 Report
A full PDF report is available here:
📄 Cyclone_Sensor_Anomaly_Report.pdf

📬 Contact
📧 For queries, contact Your Name
