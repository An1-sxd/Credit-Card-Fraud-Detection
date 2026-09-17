# Credit Card Fraud Detection

Machine learning project for detecting fraudulent credit card transactions, with a **FastAPI REST API** for predictions.

## Dataset

* 284,807 transactions
* 492 fraudulent transactions
* 30 features: `Time`, `V1`–`V28`, `Amount`
* Target: `Class` (`0` = Legit, `1` = Fraud)
* Dataset: [Kaggle Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

The dataset is not included in this repository because it exceeds GitHub's file size limit.

## ML Workflow

* Train/test split with stratification
* Undersampling of the training data
* Feature scaling with `StandardScaler`
* Logistic Regression
* Random Forest
* Evaluation using Precision, Recall, F1-score and Confusion Matrix

## API

FastAPI endpoint:

```text
POST /predict
```

The API receives a transaction's 30 features, applies the saved scaler and model, and returns:

```json
{
  "predicted_class": "legit"
}
```

or

```json
{
  "predicted_class": "fraud"
}
```

## Project Structure

```text
Credit Card Fraud Detection/
├── api/
│   └── main.py
├── model/
│   ├── model.pkl
│   └── scaler.pkl
├── notebook/
│   └── train.ipynb
├── .gitignore
└── README.md
```

## Run Locally

```bash
git clone https://github.com/An1-sxd/Credit-Card-Fraud-Detection.git
cd Credit-Card-Fraud-Detection

python -m venv venv
venv\Scripts\activate

pip install -r requirements.txt
```

Place the dataset at:

```text
data/creditcard.csv
```

Start the API:

```bash
uvicorn api.main:app --reload
```

Open Swagger:

```text
http://127.0.0.1:8000/docs
```

## Tech Stack

Python · Pandas · NumPy · Scikit-learn · FastAPI · Pydantic · Joblib
