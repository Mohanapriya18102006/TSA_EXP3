# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

Date: 02-05-2026

### AIM:

To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

### ALGORITHM:

1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
data = [29,28,21,30,31,29,25,27,25,22,27,29,28,31,30,29,25,22,27,29,24,25,29]
data = np.array(data)
N=len(data)
lags = range(35)
autocorr_values = []
mean_data = np.mean(data)
variance_data = np.var(data)
normalized_data = (data - mean_data) / np.sqrt(variance_data)
# Go through lag components one-by-one
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)  # Normalize by variance
# Display the graph
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:

<img width="994" height="637" alt="Screenshot 2026-05-02 082049" src="https://github.com/user-attachments/assets/9bfec118-8de7-47a7-9fc1-0a798a919f41" />

conclusion: exponential pattern but cycles are present.

### RESULT:

Thus we have successfully implemented the auto correlation function in python.
