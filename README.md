# Network Intrusion Detection

This project uses the CIC-IDS2017 dataset to classify network traffic as either benign or malicious. I trained and compared three machine learning models:

- Logistic regression
- Random forest
- XGBoost

The data cleaning, training, graphs, and results are all in `notebooks/intrusion_detection_model.ipynb`.

## Requirements

You will need:

- Python 3.10 or newer
- JupyterLab
- The CIC-IDS2017 CSV files
- Around 16 GB of RAM is recommended because the full dataset has about 2.8 million rows

The Python packages used in the notebook are:

- joblib
- matplotlib
- numpy
- pandas
- scikit-learn
- seaborn
- xgboost

They are also listed in `requirements.txt`.

## Dataset setup

The dataset is too large to include in this repository. Download the MachineLearningCSV version from the [CIC-IDS2017 website](https://www.unb.ca/cic/datasets/ids-2017.html).

Extract the download and place all eight CSV files in:

```text
data/raw/
```

## Installation

Open PowerShell in the project folder and create a virtual environment:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Install the required packages:

```powershell
python -m pip install -r requirements.txt
```

## Running the project

Start JupyterLab from the main project folder:

```powershell
jupyter lab
```

Open `notebooks/intrusion_detection_model.ipynb` and run the cells from top to bottom.

Training may take a while because all eight CSV files are combined and three models are trained.

## Results

XGBoost had the best result on the test data, with 99.91% accuracy and a 99.73% F1 score for malicious traffic. Random forest was very close, while logistic regression produced more false alarms.

These results came from a controlled dataset with a random train and test split, so performance on live network traffic may be different.

## Saved model

The notebook saves the best model here:

```text
models/intrusion_detector.joblib
```

The saved file also contains the scaler and feature names needed to use the model again.
