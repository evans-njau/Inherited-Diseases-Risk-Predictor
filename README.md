## Inherited Diseases Risk Dataset
### Overview

This dataset is designed for predicting the risk of inherited diseases using machine learning techniques, particularly Logistic Regression. It contains various features that represent health indicators, genetic factors, or clinical measurements, with a target variable indicating disease risk.

#### The dataset is suitable for:

- Binary classification tasks

- Medical risk prediction modeling

- Practicing data preprocessing and class balancing techniques

### Dataset Description

**File Name:** diseases.csv

**Type:** Tabular data

**Task:** Binary Classification

### Target Variable

- disease_risk

0 → No risk

1 → At risk of inherited disease

### Features

The dataset includes multiple input features (columns) representing patient-related attributes such as:

- Biological or genetic indicators

- Health measurements

- Demographic or clinical variables


### Class Distribution

The dataset initially contains class imbalance, where one class appears more frequently than the other.

### Balancing Technique Used

To address imbalance:

- Upsampling of minority class (disease_risk = 1)

- Downsampling of majority class (disease_risk = 0)

Final result:

- Balanced dataset with equal representation of both classes

### Data Preprocessing

Steps applied:

- Data visualization (histograms, correlation heatmap)

- Handling class imbalance

- Feature scaling using StandardScaler

- Train-test split (80% training, 20% testing)

### Model Usage

- The dataset is used to train a Logistic Regression model:

Models Trained:

- Unscaled Data Model

- Scaled Data Model

### Evaluation Metrics:

- Accuracy Score ~ 99%

- Confusion Matrix

- Classification Report (Precision, Recall, F1-score)

- ROC Curve & AUC Score

- Cross-validation

### Example Workflow
```
# Load dataset

data = pd.read_csv('diseases.csv')

# Split features and target
X = data.drop('disease_risk', axis=1)
y = data['disease_risk']

# Train-test split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Train model
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(X_train, y_train)
```
### Model Persistence

- The trained model is saved using joblib for reuse without retraining.

**Saving the Model:**
```
import joblib
joblib.dump(model, 'disease_risk_model.pkl')
joblib.dump(scaler, 'scaler.pkl')
```
**Loading the Model**
```
model = joblib.load('disease_risk_model.pkl')
scaler = joblib.load('scaler.pkl')
```
**Making Predictions**
```
input = [[22, 20.6, 120, 170, 3, 0]]

input_scaled = scaler.transform(pd.DataFrame(input, columns = Features.columns))
output = model.predict(input_scaled)
if output == 1:
    print("Prone to inherited diseases")
else:
    print("Not prone to inherited diseases")
```
### Requirements

- Python 3.x

- pandas

- numpy

- matplotlib

- seaborn

- scikit-learn

- joblib

### Use Cases

- Disease risk prediction

- Healthcare analytics projects

- Machine learning model evaluation practice

- Handling imbalanced datasets

### Disclaimer

- This dataset is intended for educational and research purposes only. It should not be used for real medical diagnosis or decision-making without proper validation and clinical approval.

### Author

- Developed as part of a machine learning project on Inherited Disease Risk Prediction using Logistic Regression.
