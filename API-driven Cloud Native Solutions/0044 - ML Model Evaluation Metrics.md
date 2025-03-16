### **📌 Model Evaluation Metrics for Regression and Classification**

Evaluating the performance of a machine learning model is crucial to understanding how well it can make predictions. The choice of evaluation metrics depends on whether the task is a **regression** or **classification** problem. Here’s a breakdown of common metrics for both types.

---

### **1. Model Evaluation Metrics for Regression**

In **regression tasks**, the goal is to predict a continuous value (e.g., predicting house prices, temperatures, etc.). The model’s performance is measured by how closely its predictions match the actual values.

#### **Common Regression Metrics**:

1. **Mean Absolute Error (MAE)**
   - **Formula**: 
     \[
     MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y_i}|
     \]
     Where \(y_i\) is the actual value, and \(\hat{y_i}\) is the predicted value.
   - **Interpretation**: The average absolute difference between actual and predicted values. Lower values indicate better model performance.

2. **Mean Squared Error (MSE)**
   - **Formula**: 
     \[
     MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y_i})^2
     \]
   - **Interpretation**: Measures the average squared difference between actual and predicted values. Since it squares the errors, larger errors are penalized more than smaller errors. Lower values indicate better performance.

3. **Root Mean Squared Error (RMSE)**
   - **Formula**: 
     \[
     RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y_i})^2}
     \]
   - **Interpretation**: The square root of MSE. It provides the error in the same units as the target variable, making it easier to interpret. Like MSE, larger errors are penalized more.

4. **R-squared (R²)**
   - **Formula**: 
     \[
     R^2 = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y_i})^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}
     \]
     Where \(\bar{y}\) is the mean of actual values.
   - **Interpretation**: Measures how much of the variance in the actual values is explained by the model. The value ranges from 0 to 1, where 1 means perfect prediction, and 0 means the model does not explain any variance.

5. **Mean Absolute Percentage Error (MAPE)**
   - **Formula**: 
     \[
     MAPE = \frac{1}{n} \sum_{i=1}^{n} \left| \frac{y_i - \hat{y_i}}{y_i} \right| \times 100
     \]
   - **Interpretation**: Expresses the error as a percentage of the actual value. A lower MAPE indicates better performance, but it can be biased when actual values are small.

---

### **2. Model Evaluation Metrics for Classification**

In **classification tasks**, the goal is to predict discrete class labels (e.g., spam vs. not spam, disease vs. no disease). The evaluation metrics assess how well the model distinguishes between classes.

#### **Common Classification Metrics**:

1. **Accuracy**
   - **Formula**: 
     \[
     Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
     \]
     Where:
     - \(TP\) = True Positives (correctly predicted positive)
     - \(TN\) = True Negatives (correctly predicted negative)
     - \(FP\) = False Positives (incorrectly predicted positive)
     - \(FN\) = False Negatives (incorrectly predicted negative)
   - **Interpretation**: The proportion of correct predictions to the total number of predictions. High accuracy means that most predictions are correct.

2. **Precision**
   - **Formula**: 
     \[
     Precision = \frac{TP}{TP + FP}
     \]
   - **Interpretation**: The proportion of true positive predictions to all positive predictions (i.e., how many of the predicted positives were actually positive). High precision means fewer false positives.

3. **Recall (Sensitivity, True Positive Rate)**
   - **Formula**: 
     \[
     Recall = \frac{TP}{TP + FN}
     \]
   - **Interpretation**: The proportion of actual positives that were correctly identified. High recall means fewer false negatives, but can lead to more false positives.

4. **F1-Score**
   - **Formula**: 
     \[
     F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}
     \]
   - **Interpretation**: The harmonic mean of precision and recall. F1-score balances both precision and recall, making it a good metric for imbalanced datasets.

5. **Area Under the Receiver Operating Characteristic Curve (AUC-ROC)**
   - **Formula**: AUC-ROC curve is plotted with:
     - **False Positive Rate (FPR)** on the x-axis: 
       \[
       FPR = \frac{FP}{FP + TN}
       \]
     - **True Positive Rate (TPR or Recall)** on the y-axis: 
       \[
       TPR = \frac{TP}{TP + FN}
       \]
   - **Interpretation**: The AUC is the area under the ROC curve. A higher AUC indicates a better-performing model. AUC values range from 0 to 1, with 1 being a perfect model and 0.5 indicating a model no better than random guessing.

6. **Confusion Matrix**
   - **Interpretation**: A table that shows the true positives, true negatives, false positives, and false negatives. It provides a more detailed view of model performance and is useful for calculating other metrics like precision, recall, and F1-score.

7. **Logarithmic Loss (Log Loss)**
   - **Formula**: 
     \[
     Log Loss = - \frac{1}{n} \sum_{i=1}^{n} [y_i \log(\hat{y_i}) + (1 - y_i) \log(1 - \hat{y_i})]
     \]
     Where \(y_i\) is the true label and \(\hat{y_i}\) is the predicted probability.
   - **Interpretation**: Measures the uncertainty of the model’s predictions based on how close the predicted probabilities are to the actual class labels. Lower values indicate better predictions.

---

### **📌 Summary Table of Evaluation Metrics**

| **Metric**                  | **Type**            | **Description**                                                                 |
|-----------------------------|---------------------|---------------------------------------------------------------------------------|
| **MAE (Mean Absolute Error)**| Regression          | Average of the absolute differences between predicted and actual values.         |
| **MSE (Mean Squared Error)** | Regression          | Average of squared differences between predicted and actual values.             |
| **RMSE (Root Mean Squared Error)** | Regression    | Square root of MSE. More interpretable, penalizes larger errors more.           |
| **R² (R-Squared)**          | Regression          | Proportion of variance explained by the model (0 to 1).                         |
| **Accuracy**                | Classification      | Percentage of correct predictions (overall correctness).                        |
| **Precision**               | Classification      | Percentage of true positives out of all predicted positives.                    |
| **Recall**                  | Classification      | Percentage of actual positives that were correctly identified.                  |
| **F1-Score**                | Classification      | Harmonic mean of precision and recall.                                         |
| **AUC-ROC**                 | Classification      | Area under the ROC curve, indicating the model’s ability to discriminate classes.|
| **Log Loss**                | Classification      | Measures uncertainty in predictions, penalizes wrong probabilities.             |

---

### **📌 Conclusion**

Choosing the right evaluation metric depends on the problem you're working on. In regression tasks, metrics like MAE, MSE, and R² help evaluate the model's accuracy in predicting continuous values. For classification tasks, precision, recall, accuracy, and F1-score are commonly used to assess how well the model distinguishes between different classes.
