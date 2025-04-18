*** Heart Disease Prediction Project using the heart.csv Dataset ***


### Dataset Overview: 

The heart.csv dataset contains various medical attributes related to heart disease. The goal of this project is to predict the likelihood of heart disease based on the given features. The dataset contains the following 
columns:
Age: The age of the patient.
Sex: Gender of the patient (male or female).
ChestPainType: The type of chest pain experienced by the patient.
RestingBP: Resting blood pressure (mm Hg).
Cholesterol: Serum cholesterol level.
FastingBS: Fasting blood sugar level (1 if greater than 120 mg/dl, else 0).
RestingECG: Resting electrocardiographic results.
MaxHR: Maximum heart rate achieved during exercise.
ExerciseAngina: Indicates whether the patient experienced exercise-induced angina.
Oldpeak: Depression induced by exercise relative to rest.
ST_Slope: The slope of the peak exercise ST segment.
HeartDisease: Target variable (1 if the patient has heart disease, 0 otherwise).

### Project Steps:

## Exploratory Data Analysis (EDA):

I started by performing EDA on the dataset to explore the distribution and relationships of each feature. This step helped to identify patterns and potential issues, such as missing data and outliers.

1) Label Encoding:

Categorical variables (like Sex, ChestPainType, RestingECG, ExerciseAngina, and ST_Slope) were encoded using LabelEncoder to convert them into numerical values for machine learning algorithms.

2) Handling Missing Data:

I identified missing values in the dataset and imputed them using the mean of the respective columns. This ensured that the dataset was complete for training the model.

3) Data Scaling:

I applied StandardScaler to scale the features so that all values were on the same scale. This is important for algorithms that are sensitive to the scale of input features, such as gradient boosting models.

4) Splitting Data:

The dataset was divided into independent features (X) and the target variable (HeartDisease) (y). I then split the data into training and testing sets.

5) Model Building:

I first used the CatBoost algorithm for classification. I set the following hyperparameters:
Learning Rate: 0.05
Number of Iterations: 1000
Max Depth: 5
I used Recall as the evaluation metric to prioritize minimizing false negatives (missed heart disease diagnoses).
The model achieved 91% accuracy on the test data.

6) Confusion Matrix:

I visualized the confusion matrix to understand the model's performance:
89 instances were correctly predicted as non-diseased.
9 non-diseased instances were wrongly predicted as diseased.
11 diseased instances were wrongly predicted as non-diseased.
121 diseased instances were correctly predicted as diseased.

7) Cross-Validation:

I applied cross-validation to evaluate the model's robustness. The cross-validation score was consistent with the performance achieved on the test set.

8) Feature Importance:

I generated a feature importance plot using the CatBoost model to see which features contributed the most to predicting heart disease. Features like Age, Cholesterol, and MaxHR were identified as important.

9) ROC Curve:

I plotted the ROC Curve and calculated the AUC (Area Under the Curve). The AUC score was 91%, which indicates a good model performance.

10) Noise Filtering with LOF (Local Outlier Factor):

To assess whether filtering noise would improve the model's performance, I applied the LOF (Local Outlier Factor) technique to remove noisy data points.
After filtering the noisy data, I retrained the model, but the accuracy decreased to 89%, suggesting that the removal of noisy data did not improve, and potentially harmed, the model's performance.

11) Saving the Model:

Finally, I saved the trained CatBoost model along with the LabelEncoder for categorical features and the Scaler used to scale the data. This allows the model to be reused in the future with new data.


## Conclusion:

This project demonstrates how machine learning techniques can be applied to predict heart disease based on medical features. The CatBoost algorithm performed well, achieving high accuracy, and various techniques such as Label Encoding, Standard Scaling, and Noise Filtering were explored to improve model performance. The final model, despite noise filtering reducing performance, was effective in predicting heart disease and is ready for deployment in healthcare applications.
