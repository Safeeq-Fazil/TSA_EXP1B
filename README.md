## Developed By: SAFEEQ FAZIL A
## Register no : 212222240086
## Date: 

# Ex.No: 1B  CONVERSION OF NON STATIONARY TO STATIONARY DATA

### AIM:
To perform regular differncing,seasonal adjustment and log transformation on vegetable price data.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
   
### PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
from statsmodels.tsa.stattools import adfuller

# Load the dataset
file_path = '/content/vegpred.csv' 
data = pd.read_csv(file_path)

# Convert the 'Date' column to datetime format
data['Date'] = pd.to_datetime(data['Date'])

# Filter data for a specific commodity (e.g., "Potato Red")
commodity_name = 'Potato Red' 
commodity_data = data[data['Commodity'] == commodity_name].set_index('Date')

# Selecting the 'Average' price for analysis
time_series = commodity_data['Average']

# Plot the original time series
plt.figure(figsize=(10, 6))
plt.plot(time_series, marker='o')
plt.title(f'Original Time Series - {commodity_name}')
plt.xlabel('Date')
plt.ylabel('Average Price (in Rs)')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Regular Differencing (to remove trend)
differenced = time_series.diff().dropna()

# Seasonal Adjustment (if applicable, assuming 12 months for annual seasonality)
seasonally_adjusted = time_series.diff(12).dropna()

# Log Transformation (to stabilize variance)
log_transformed = np.log(time_series)
log_transformed_diff = log_transformed.diff().dropna()

# Plotting the transformations
fig, ax = plt.subplots(3, 1, figsize=(12, 12))

# Plot Differenced Series
ax[0].plot(differenced, marker='o', color='blue')
ax[0].set_title('Regular Differencing')
ax[0].set_xlabel('Date')
ax[0].set_ylabel('Differenced Price')
ax[0].grid(True)

# Plot Seasonally Adjusted Series
ax[1].plot(seasonally_adjusted, marker='o', color='green')
ax[1].set_title('Seasonal Differencing')
ax[1].set_xlabel('Date')
ax[1].set_ylabel('Seasonally Adjusted Price')
ax[1].grid(True)

# Plot Log Transformed and Differenced Series
ax[2].plot(log_transformed_diff, marker='o', color='red')
ax[2].set_title('Log Transformation with Differencing')
ax[2].set_xlabel('Date')
ax[2].set_ylabel('Log Differenced Price')
ax[2].grid(True)

plt.tight_layout()
plt.show()
```

### OUTPUT:
## Original TimeSeries:
![image](https://github.com/user-attachments/assets/23823674-bb6b-422d-bda4-9589afb97ffe)


## REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/8e904e43-4c42-47e8-a90a-610080e9f562)


## SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/8bd39de0-29a6-4640-9377-4cff0684924e)


## LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/3930178e-2c55-4e7e-8944-51df03351815)



### RESULT:
Thus the python code has created for the conversion of non stationary to stationary data on vegetable price data.
