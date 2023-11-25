**Root Mean Squared Error (RMSE): Overview and Formula**

### Overview:

Root Mean Squared Error (RMSE) is a widely used metric for evaluating the accuracy of a regression model. It provides a measure of the average magnitude of the errors between predicted and actual values, with a higher weight given to larger errors. RMSE is particularly useful when the errors are expected to be normally distributed.

### Formula:

The RMSE is calculated using the following formula:

\[ RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (Y_i - \hat{Y}_i)^2} \]

- \( n \) is the number of observations.
- \( Y_i \) is the actual value for the ith observation.
- \( \hat{Y}_i \) is the predicted value for the ith observation.

### Key Points:

1. **Squared Differences:**
   - The differences between actual and predicted values are squared to emphasize larger errors.
   - Squaring also ensures that negative and positive errors do not cancel each other out.

2. **Mean Squared Error (MSE):**
   - RMSE is the square root of the mean squared error (MSE).
   - MSE is calculated by averaging the squared differences between actual and predicted values.

3. **Rooting the Mean:**
   - Taking the square root of the mean squared error gives a measure in the same units as the target variable, making it more interpretable.

### Interpretation:

- RMSE values range from 0 to infinity.
- A lower RMSE indicates better model performance, with 0 being a perfect fit (predicted values match actual values).
- It is sensitive to outliers and penalizes large errors more heavily than smaller errors.

### Example:

Let's use a Python example to calculate the RMSE:

```python
import numpy as np
from sklearn.metrics import mean_squared_error

# Actual values
actual_values = np.array([2, 5, 7, 9, 11])

# Predicted values
predicted_values = np.array([1.8, 4.5, 6.5, 9.2, 11.5])

# Calculate RMSE using scikit-learn's mean_squared_error function
mse = mean_squared_error(actual_values, predicted_values)
rmse = np.sqrt(mse)

print("Mean Squared Error (MSE):", mse)
print("Root Mean Squared Error (RMSE):", rmse)
```

In this example, we have actual values and corresponding predicted values. We use the `mean_squared_error` function from scikit-learn to calculate the mean squared error, and then take the square root to obtain the RMSE. The lower the RMSE, the better the model's predictive performance.
