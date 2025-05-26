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

## 🧾 File Outputs

- `flights_with_pred reduced_for_git.csv`:  
  Contains the final dataset with model predictions (`prediction` = 0 or 1) and `prob_delayed` score for future deployment or visualization in Power BI. reduced size for git.

- `flightsjan2025.csv`:  
  CSV File containing all the original flight information used in the beginning of the notebook.

- `noaa_weather_2025/`:  
  Full set of NOAA weather files initially downloaded and processed.

## 🔮 Prediction Function

The notebook includes a `predict_delay()` function for custom inputs:

```python
predict_delay(
    airline='AA',
    origin='JFK',
    destination='LAX',
    dep_hour=15,
    day_of_week=5,
    is_weekend=0,
    air_temp=30.0,
    wind_speed=5.2,
    precip=0.0
)
✈️ Prediction: DELAYED (class=1) - Probability of delay: 0.53
(np.int64(1), np.float32(0.5275923))
```

## 📊 Visualizations

Delay rate was explored across:
- **Hour of day**: early mornings had fewer delays; late afternoons had more
![Screenshot 2025-05-26 at 10 43 36 AM](https://github.com/user-attachments/assets/d01b9e29-f272-4a50-b657-2039ed0d275a)
- **Top origin airports**: some (like DFW, DEN) showed higher delay rates
![Screenshot 2025-05-26 at 10 44 08 AM](https://github.com/user-attachments/assets/83c89a4f-8a36-4ff9-b740-480ec4693dc7)
- **Top airlines**: delay rates varied across carriers
![Screenshot 2025-05-26 at 10 44 32 AM](https://github.com/user-attachments/assets/1dac7d22-71ab-4116-852d-760ce2d92d76)

## 🔍 Data Sources

- **Flight data:** U.S. Bureau of Transportation Statistics (BTS)
- **Weather data:** NOAA ISD historical hourly reports
- **Real-time sampling:** AviationStack API (for experimentation only)

## 🧠 Next Steps

- Expand beyond January to improve generalization
- Engineer more time-related or weather features (e.g. visibility, storm flags)
- Deploy a live version with real-time predictions
