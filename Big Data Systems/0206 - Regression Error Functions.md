Regression error functions, also known as loss or cost functions, measure the difference between the predicted values of a regression model and the actual values. These functions help in assessing how well the model is performing and guide the process of optimizing the model parameters. The goal is typically to minimize the error function.

Here are some common regression error functions:

### 1. **Mean Squared Error (MSE):**
   - **Formula:**
     \[ MSE = \frac{1}{n} \sum_{i=1}^{n} (Y_i - \hat{Y}_i)^2 \]
   - **Description:**
     - \(Y_i\) is the actual value for the ith observation.
     - \(\hat{Y}_i\) is the predicted value for the ith observation.
     - Squaring the errors emphasizes larger errors and penalizes them more.

### 2. **Mean Absolute Error (MAE):**
   - **Formula:**
     \[ MAE = \frac{1}{n} \sum_{i=1}^{n} |Y_i - \hat{Y}_i| \]
   - **Description:**
     - MAE represents the average absolute difference between actual and predicted values.
     - It is less sensitive to outliers compared to MSE.

### 3. **Mean Squared Logarithmic Error (MSLE):**
   - **Formula:**
     \[ MSLE = \frac{1}{n} \sum_{i=1}^{n} (\log(1 + Y_i) - \log(1 + \hat{Y}_i))^2 \]
   - **Description:**
     - It is useful when the target variable has a large range.
     - It penalizes underestimates more than overestimates.

### 4. **Root Mean Squared Error (RMSE):**
   - **Formula:**
     \[ RMSE = \sqrt{MSE} \]
   - **Description:**
     - RMSE is the square root of the MSE.
     - It is in the same units as the target variable, making it more interpretable.

### 5. **Huber Loss:**
   - **Formula:**
     \[ L_{\delta}(r) = \begin{cases} \frac{1}{2} r^2 & \text{for } |r| \leq \delta \\ \delta(|r| - \frac{1}{2}\delta) & \text{otherwise} \end{cases} \]
   - **Description:**
     - It is less sensitive to outliers than MSE.
     - It behaves quadratically for small errors and linearly for large errors.

### 6. **Quantile Loss:**
   - **Formula:**
     \[ L_q(r) = \begin{cases} q \cdot r & \text{if } r \geq 0 \\ (q-1) \cdot r & \text{otherwise} \end{cases} \]
   - **Description:**
     - It is used for quantile regression, allowing different loss functions for positive and negative errors.

### 7. **Poisson Deviance:**
   - **Formula:**
     \[ D(y, \hat{y}) = 2 \sum_{i=1}^{n} \left(y_i \cdot \log\left(\frac{y_i}{\hat{y}_i}\right) - (y_i - \hat{y}_i)\right) \]
   - **Description:**
     - It is suitable for count data when the target variable follows a Poisson distribution.

### 8. **R-squared (Coefficient of Determination):**
   - **Formula:**
     \[ R^2 = 1 - \frac{\sum_{i=1}^{n} (Y_i - \hat{Y}_i)^2}{\sum_{i=1}^{n} (Y_i - \bar{Y})^2} \]
   - **Description:**
     - Represents the proportion of variance explained by the model.
     - Ranges from 0 to 1, where 1 indicates a perfect fit.

The choice of the error function depends on the characteristics of the data and the goals of the modeling task. Optimization techniques aim to minimize these error functions during the training of regression models.
