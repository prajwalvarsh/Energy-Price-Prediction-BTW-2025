# Energy Price Prediction - BTW 2025 Data Science Challenge

## Project Overview

This project was developed for the BTW 2025 Data Science Challenge focused on predicting energy prices in the German electricity market. The goal is to forecast day-ahead electricity prices using historical data and various external factors that influence energy pricing.

## Team Members

**Group 2:**
- **Meike Bauer** - Domain Knowledge, Data Analysis, and Visualization
- **Prajwal Amoghavarsh** - Predictive Modeling

## Project Structure

The project is organized into four main phases:

### Phase 1: Gathering Domain Knowledge & Data Sources
- Analysis of German energy market structure
- Understanding price formation mechanisms
- Identification of relevant data sources
- Study of energy sources and market dynamics

### Phase 2 & 3: Data Cleaning, Exploratory Data Analysis, Visualization & Storytelling
- Data preprocessing and cleaning
- Exploratory analysis of energy price patterns
- Visualization of trends and correlations
- Data storytelling and insights

### Phase 4: Predictive Modelling
- LSTM-based neural network implementation
- Feature engineering and data preparation
- Model training and validation
- Performance evaluation using RMSE

### Limitations and Future Work
- Analysis of current approach limitations
- Suggestions for improvements
- Discussion of additional data sources

## Data Sources

The project incorporates multiple data sources:

1. **Historical Energy Prices** (SMARD - Strommarktdaten)
   - Day-ahead electricity prices from 2020-2024
   - Hourly resolution data

2. **Weather Data** (Deutsche Wetterdienst - DWD)
   - Air temperature
   - Wind speed
   - Minutes of sunshine per hour
   - Data from 16 weather stations (one per German state)

3. **Energy Generation and Consumption Data** (SMARD)
   - Forecasted energy consumption
   - Generation from various sources (wind, solar, etc.)
   - Residual load data

## Methodology

### Data Preprocessing
- **Log Transformation**: Applied to handle negative prices and outliers
- **Scaling**: MinMaxScaler used for feature normalization
- **Weather Data Aggregation**: Mean values calculated across 16 weather stations

### Model Architecture
- **LSTM Neural Network**: Sequential architecture with LSTM layers
- **Features**: Wind generation, consumption, residual load, weather variables
- **Training**: Adam optimizer with MSE loss function
- **Sequence Length**: Optimized for temporal dependencies

### Performance Metrics
- **RMSE (Root Mean Square Error)**: 3.2617
- Evaluation performed on February 5, 2025 predictions

## Key Results

The LSTM model successfully predicts day-ahead electricity prices with:
- RMSE of 3.2617 on test data
- Ability to capture both short-term fluctuations and long-term trends
- Integration of multiple weather and energy generation features

## Requirements

```python
# Core libraries
pandas
numpy
matplotlib
seaborn
scikit-learn
torch
tensorflow/keras

# Weather data processing
requests
zipfile
datetime
```

## File Structure

```
├── submission_group_2.ipynb    # Main notebook with complete analysis
├── README.md                   # This file
├── combined_data.csv          # Processed dataset
├── Electricity_Forecasted_Prices.csv
├── final_dataset_SunHours_SD_SO.csv
├── final_dataset_Temperature_TT_TU.csv
└── final_dataset_Wind_F.csv
```

## Usage

1. **Data Preparation**: Run the data preprocessing sections to clean and merge all datasets
2. **Exploratory Analysis**: Execute visualization cells to understand data patterns
3. **Model Training**: Train the LSTM model using the prepared features
4. **Prediction**: Generate forecasts for future dates
5. **Evaluation**: Calculate RMSE and other performance metrics

## Key Insights

1. **Market Dynamics**: German energy prices are heavily influenced by renewable energy generation and weather conditions
2. **Volatility**: Energy prices show significant volatility with notable price spikes during certain periods
3. **Feature Importance**: Weather variables (wind, temperature, sunshine) are crucial predictors alongside energy generation data
4. **Model Performance**: LSTM effectively captures temporal dependencies in energy price data

## Limitations and Future Improvements

### Current Limitations
1. **Weather Forecasts**: Model uses historical weather data instead of weather forecasts
2. **Fossil Fuel Prices**: Limited availability of fossil fuel price data
3. **Computational Complexity**: LSTM training is computationally expensive

### Suggested Improvements
1. **Weather Integration**: Use weather forecasts or moving averages of previous days
2. **Fossil Fuel Data**: Include gas and coal price data when available
3. **Model Enhancement**: Implement hyperparameter optimization and explainable AI techniques
4. **Multiple Models**: Compare LSTM performance with other time-series models

## Technical Implementation

The project demonstrates:
- Advanced time-series forecasting techniques
- Multi-variate feature engineering
- Deep learning model implementation
- Data visualization and storytelling
- Domain-specific knowledge application

## References

- Bundesnetzagentur (Federal Network Agency)
- German Federal Ministry for Economic Affairs and Climate Action (BMWK)
- International Energy Agency (IEA)
- Agora Energiewende
- Malte Lehna, Fabian Scheller, and Helmut Herwartz. "Forecasting day-ahead electricity prices: A comparison of time series and neural network models taking external regressors into account." Energy Economics, 106:105742, 2022.

## Contact

For questions or remarks about specific parts of the project, please refer to the respective contributor:
- Domain Knowledge & Data Analysis: Meike Bauer
- Predictive Modeling: Prajwal Amoghavarsh