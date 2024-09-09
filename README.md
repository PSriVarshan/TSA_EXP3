### Developed by : Sri Varshan P
### Register No.: 212222240104
### Date :

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the tank losses in Russian War

### ALGORITHM:

1. Import the necessary packages

2. Find the mean, variance and then implement normalization for the data.

3. Implement the correlation using necessary logic and obtain the results

4. Store the results in an array

5. Represent the result in graphical representation as given below.

### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the CSV file
file_path = 'russia_losses_equipment.csv'
data = pd.read_csv(file_path)

# Extract the 'tank' data
tank_data = data['tank'].dropna().values

# Mean
data_mean = np.mean(tank_data)

# Variance
data_var = np.var(tank_data)

# Normalized data
normalized_data = (tank_data - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) of Tank Losses')
plt.show()


```
### OUTPUT:

![image](https://github.com/user-attachments/assets/caa23d2d-8613-4f92-871a-b37f4169319c)


#### Autocorrelation Function (ACF) of Tank Losses

![image](https://github.com/user-attachments/assets/77893c0e-0b4f-4012-9297-3c41f8054a5b)



### RESULT:

####     Thus auto correlation function in python is successfully implemented.
