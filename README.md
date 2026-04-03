# 🚉 KTM Komuter Ridership Forecasting
🎓 WIA1006 Machine Learning - Group Assignment
## 📌 Project Overview
This project develops a high-precision **regression model** to forecast train boardings at individual KTM Komuter stations for the **next hour**. By integrating historical ridership with real-time weather and holiday data, the model captures complex urban mobility patterns.

## 🛠️ Technical Workflow

### 1. Multi-Source Data Acquisition
* **Web Scraping (`BeautifulSoup`):** Extracted Malaysian public holiday schedules to account for national and state-specific ridership fluctuations.
* **Geospatial Processing (`Geopy`):** Used **Nominatim** to convert station names into precise Latitude/Longitude coordinates.
* **Weather Integration (`NASA POWER API`):** Retrieved historical hourly weather (Temperature, Humidity, Wind Speed, Precipitation) for each station's location.

### 2. Feature Engineering
* **Temporal Logic:** Engineered **Rush Hour** (7-8 AM, 5-6 PM) and **Holiday** boolean flags.
* **Lagged Variables:** Generated `Ridership_Lag1` (previous hour) and `Ridership_Lag24` (previous day) to capture short-term and cyclical trends.

### 3. Model Optimization
* **Model Candidates:** Evaluated **LightGBM, XGBoost, CatBoost, HistGradientBoosting,** and **Random Forest**.
* **Tuning Strategy:** Utilized `RandomizedSearchCV` paired with `TimeSeriesSplit` cross-validation to maintain temporal data integrity during training.

---

## 📈 Evaluation & Results
The model was validated using a **80/20 Temporal Split** (training on past data, testing on future periods). Performance was measured using:
* **MSE** (Mean Squared Error)
* **RMSE** (Root Mean Squared Error)
* **R² Score** (Coefficient of Determination)
