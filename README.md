# Ocean Wave Height Prediction with LSTM

This project uses an LSTM (Long Short-Term Memory) neural network to predict significant wave height (`wave_ht_sig`) based on various environmental variables, including wind speed, air pressure, air temperature, and surface temperature. The goal is to develop a model that forecasts wave heights accurately, which is valuable for marine safety, navigation, and oceanographic research.

## Project Overview

Predicting wave height is challenging due to the variability in ocean conditions and the impact of extreme weather events. This project leverages time series data from a marine station to train an LSTM model for short-term wave height forecasting. By understanding wave patterns, this project contributes to improved safety and operational planning for activities dependent on ocean conditions.

## Dataset

The dataset used in this project is sourced from the [SmartAtlantic Halifax Buoy Dataset](https://www.smartatlantic.ca/erddap/tabledap/SMA_halifax.html) provided by SmartAtlantic’s ERDDAP (Environmental Research Division Data Access Program) portal. It offers real-time and historical oceanographic and meteorological data collected by a buoy located in Halifax, Nova Scotia. Key details about this dataset include:

- **Source**: [SmartAtlantic Halifax Buoy Dataset](https://www.smartatlantic.ca/erddap/tabledap/SMA_halifax.html)
- **Variables**:
  - `wind_spd_avg` - Average wind speed (m/s)
  - `wind_spd_max` - Maximum wind speed (m/s)
  - `wind_dir_avg` - Average wind direction (degrees)
  - `air_temp_avg` - Average air temperature (°C)
  - `air_pressure_avg` - Average air pressure (mbar)
  - `surface_temp_avg` - Sea surface temperature (°C)
  - `wave_ht_max` - Maximum wave height (m)
  - `wave_ht_sig` - Significant wave height (m)
  - `wave_dir_avg` - Average wave direction (degrees)
- **Time Range**: The dataset covers a continuous time series with hourly updates, allowing for detailed temporal analysis of ocean conditions.
- **Geographical Location**: Halifax, Nova Scotia, a strategic location for maritime operations along the Atlantic coast of Canada.
- **Applications**: This data is instrumental for marine forecasting, navigation safety, environmental monitoring, and climate research in the Atlantic region.

## Project Structure

- **Data Preprocessing**:
  - Missing values were handled, and the data was scaled using MinMaxScaler for each feature.
  - The target variable (`wave_ht_sig`) was scaled separately to facilitate inverse transformation after prediction.
- **Sequence Creation**: 60-timestep sequences were created for multivariate time series input to the LSTM model.
- **Model Architecture**: A sequential LSTM model was implemented with:
  - Two LSTM layers, each with 50 units.
  - Dense layers for output, optimized using mean squared error loss and Adam optimizer.

## Model Training and Evaluation

The model was trained on 80% of the dataset, with the remaining 20% reserved for testing. Key metrics:
- **Root Mean Squared Error (RMSE)**: The model achieved an RMSE of approximately 0.346 on the test set.
- **Performance Analysis**: The model captures general trends in wave heights but struggles with peak wave heights, indicating potential areas for improvement.

## Results

- **Plot**: The plot of actual vs. predicted wave heights shows the model can generally follow the trend of wave height changes but underperforms on extreme events.
- **Interpretation**: While the model provides a reasonable forecast, capturing rare peaks accurately requires additional model tuning or more extensive data.

## Conclusion

This project presents a foundational approach to predicting wave heights using an LSTM model, offering a pathway for more advanced marine forecasting applications. Although the model effectively captures general wave trends, further improvements are suggested to enhance accuracy, particularly for extreme wave events.
