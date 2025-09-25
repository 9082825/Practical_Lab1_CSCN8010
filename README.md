# Practical_Lab1_CSCN8010  
# Data Analysis & Anomaly Detection  

This project processes sensor data (time-series, multiple axes) to detect anomalies using regression, residuals, and threshold-based alerts.  

---

##  Workflow  

### 1. Data Ingestion  
- **From DB (Neon.tech PostgreSQL)** using SQLAlchemy/psycopg2.   

Dataset includes:  
- A **time column**  
- Multiple **axis columns** (`Axis1`–`Axis8`)  

---

### 2. Preprocessing  
- Converted `time` → datetime  
- Sorted by time  
- Handled missing values (drop/fill)  
- Scale values:  
  - **Min-Max** `[0,1]`  
  - **Z-score** `(x - mean) / std`  

---

### 3. Regression Modeling  
- Fit **Linear Regression** per axis:  
  - `X` = time (index)  
  - `y` = sensor readings  
- Saved slope & intercept  
- Ploted scatter + regression lines  

---

### 4. Residual Analysis  
- Computed residuals = observed – predicted  
- Visualized:  
  - Scatter plot  
  - Histogram  
  - Boxplot  
- Identified **outliers**  

---

### 5. Threshold Discovery  
- **MinC** = mean + 2σ  
- **MaxC** = mean + 3σ  
- **T** = minimum persistence time (seconds)  

---

### 6. Alerts & Errors  
- **Alert** → residual ≥ MinC for ≥ T seconds  
- **Error** → residual ≥ MaxC for ≥ T seconds  
- Log details:  
  - Event type (Alert/Error)  
  - Axis number  
  - Start & end time  
  - Duration  
- Saved in: `results/logs.csv`  

---

### 7. Synthetic Data  
- Generated test data with same mean/std as training data  
- Injected spikes to simulate anomalies  
- Validated pipeline  

---

### 8. Visualization  
- For each axis:  
  - Raw data + regression line  
  - Alerts  & Errors 
- Residual plots with thresholds  
- Saved in: `results/regression_plots/`  

---

##  Outputs  
- **Logs** → `results/logs.csv`  
- **Plots** → `results/regression_plots/`  
- **Notebook** → `main.ipynb` 

---
