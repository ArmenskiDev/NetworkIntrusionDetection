# Network Intrusion Detection

This is a machine learning project that uses network-flow data to identify malicious traffic. I used the CIC-IDS2017 dataset and compared three binary classifiers:

- Logistic regression
- Random forest
- XGBoost

The full analysis is in `notebooks/intrusion_detection_model.ipynb`.

## Dataset

The dataset is not included in the repository because the CSV files are large. Download the MachineLearningCSV version of [CIC-IDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) and place the eight CSV files in `data/raw/`.

The notebook combines the files, removes invalid and duplicate rows, and changes the original labels into two classes:

- `0`: benign traffic
- `1`: malicious traffic

## Running the notebook

Create a virtual environment and install the packages:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Then open Jupyter and run the notebook from top to bottom:

```powershell
jupyter lab
```

Training all three models takes a while because the combined dataset has about 2.8 million rows.

## Results

On the saved 20% test split, XGBoost gave the best malicious-class F1 score (99.73%). Random forest was close behind, while logistic regression had more false positives. These results are for the CIC-IDS2017 lab dataset and may not carry over to live network traffic.

The notebook saves the selected model to `models/intrusion_detector.joblib`. Generated model files are ignored by Git.
