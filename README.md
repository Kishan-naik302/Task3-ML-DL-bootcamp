#  Week 3 Task — Ensemble Model Comparison

Comparing three ensemble learning models to predict hourly interstate traffic volume using weather, time, and holiday data.



##  Dataset

**Metro Interstate Traffic Volume** — UCI Machine Learning Repository #492

- 48,204 hourly records of westbound traffic on Interstate 94, Minnesota
- Download: https://archive.ics.uci.edu/dataset/492/metro+interstate+traffic+volume
- After downloading, place `Metro_Interstate_Traffic_Volume.csv` in the project folder
- If the file is not found, the script automatically falls back to a synthetic dataset with the same structure

##  Models Compared

| Model | Description |
|---|---|
| **Random Forest** | Builds many decision trees independently and averages their predictions |
| **AdaBoost** | Builds trees sequentially, each one focusing on the previous model's mistakes |
| **XGBoost** | Optimised gradient boosting with regularisation — fast and highly accurate |


##  Requirements & Installation

Make sure you have Python 3.8+ installed, then run:

```bash
pip install numpy pandas scikit-learn xgboost matplotlib seaborn reportlab Pillow
``

##  How to Run

### Option A — Python Script
```bash
# Step 1: Run the model comparison (trains models + saves charts)
python traffic_model_comparison.py

# Step 2: Generate the PDF report
python generate_report.py
```

### Option B — Jupyter Notebook
```bash
jupyter notebook traffic_model_comparison.ipynb
```
Then run all cells from top to bottom (Cell → Run All).

##  Project Structure

```
├── traffic_model_comparison.py       # Main script: trains models, evaluates, plots charts
├── traffic_model_comparison.ipynb    # Jupyter notebook version (17 cells)
├── generate_report.py                # Generates the PDF report from results
├── Week3_Ensemble_Models_Report.pdf  # Final PDF report (output)
├── metro_traffic.csv                 # Synthetic fallback dataset
├── metrics_comparison.png            # Bar chart: MAE, RMSE, R², training time
├── scatter_comparison.png            # Predicted vs Actual scatter plots
├── feature_importance.png            # Feature importance charts
└── README.md                         # This file
```

##  Results

| Model | MAE | RMSE | R² Score | Train Time |
|---|---|---|---|---|
| Random Forest | 320.0 | 400.9 | 0.8691 | 9.9s |
| AdaBoost | 345.4 | 433.5 | 0.8469 | 5.9s |
| **XGBoost** | **317.9** | **398.7** | **0.8705** | **0.3s** |

> ✅ **Lower MAE/RMSE = better** &nbsp;|&nbsp; ✅ **Higher R² = better** &nbsp;|&nbsp; ✅ **Lower Train Time = better**

##  Key Findings

- **XGBoost** is the overall winner — best accuracy across all three metrics and trains **30x faster** than Random Forest
- **Random Forest** is a close second in accuracy and easier to explain to non-technical audiences
- **AdaBoost** is slightly behind on this dataset but remains a solid choice for clean, outlier-free data
- The most influential features are **hour of day**, **day of week**, and **temperature** — time matters more than weather for traffic prediction

 Output Files

After running the scripts, the following files will be generated:

- `metrics_comparison.png` — side-by-side bar charts of all evaluation metrics
- `scatter_comparison.png` — predicted vs actual scatter plots for each model
- `feature_importance.png` — feature importance rankings (Random Forest & XGBoost)
- `Week3_Ensemble_Models_Report.pdf` — full formatted report with charts and analysis

**Course:** Machine Learning  
**Task:** Week 3 — Ensemble Methods  
**Dataset:** Metro Interstate Traffic Volume (UCI ML Repo ID 492)  
**Models:** scikit-learn (Random Forest, AdaBoost) + XGBoost
