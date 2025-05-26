# ✈️ Flight Delay Predictor

This project predicts flight delays using operational and weather data from U.S. domestic flights in January 2025.

## 🧪 Models Tested

- **Random Forest (Baseline):**  
  - Accuracy: ~77%  
  - Missed many actual delays (low recall)

- **Random Forest + Class Balancing:**  
  - Accuracy: ~69%  
  - Higher recall for delayed flights (≈30%)

- **Random Forest + Weekend Feature:**  
  - Slight improvement from adding `is_weekend`  
  - Showed small but valid impact

- **Random Forest + Weather Data:**  
  - Accuracy: ~80.5%  
  - Key features: destination, air_temp, origin  
  - Weather helped; `1hr_precip` and `is_weekend` had lower impact

- **XGBoost Classifier:**  
  - Accuracy: ~54%  
  - Much higher recall for delayed flights (≈76%)  
  - Best when catching delays is more important than overall accuracy

## 📊 Visualizations

Delay rate was explored across:
- **Hour of day**: early mornings had fewer delays; late afternoons had more
- **Top origin airports**: some (like DFW, DEN) showed higher delay rates
- **Top airlines**: delay rates varied across carriers
- **1-hour precipitation**: weak/noise-heavy relationship, excluded from dashboard

## 🔍 Data Sources

- **Flight data:** U.S. Bureau of Transportation Statistics (BTS)
- **Weather data:** NOAA ISD historical hourly reports
- **Real-time sampling:** AviationStack API (for experimentation only)

## 🧠 Next Steps

- Expand beyond January to improve generalization
- Engineer more time-related or weather features (e.g. visibility, storm flags)
- Deploy a live version with real-time predictions
