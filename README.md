# methane-detection
Methane presence classification using gas sensor data and a Decision Tree machine learning model.
# Methane Detection Using a Decision Tree Classifier

## Overview

This project explores methane-presence classification using gas sensor data and a Decision Tree machine learning model.

The notebook processes gas sensor measurements, creates a binary target based on methane concentration, trains a classifier, evaluates its predictions, and exports the trained model.

## Objectives

- Load and inspect gas sensor measurements.
- Prepare data for machine learning.
- Select sensor readings as input features.
- Create a binary methane-presence target.
- Train a Decision Tree classifier.
- Evaluate classification performance.
- Extract decision rules and save the trained model.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Joblib
- Jupyter Notebook

## Dataset

The notebook references `ethylene_methane.txt` from the Gas Sensor Array Under Dynamic Gas Mixtures dataset.

The expected columns in the final modeling section are:

- `time_s` — Time measurement
- `Methane_ppm` — Methane concentration
- `Ethylene_ppm` — Ethylene concentration
- `s1` through `s16` — Sensor readings

The dataset must be obtained separately. Update the file path and verify the column structure before running the notebook.

## Methodology

### 1. Data Loading

The dataset is loaded using Pandas with whitespace-separated parsing. The notebook assigns column names and inspects the resulting data.

### 2. Feature Selection

The final modeling section uses three sensor features:

- `s1`
- `s5`
- `s8`

### 3. Target Creation

The `Methane_ppm` column is converted into a binary target:

- `1`: Methane concentration is greater than zero.
- `0`: Methane concentration is zero or less.

The model therefore predicts methane presence rather than exact concentration.

### 4. Train-Test Split

The dataset is split into training and testing sets using an 80:20 ratio and `random_state=42`.

### 5. Decision Tree Model

The classifier uses the following parameters:

- Maximum depth: 6
- Minimum samples to split: 1,000
- Minimum samples per leaf: 500
- Pruning parameter (`ccp_alpha`): 0.0005
- Random state: 42

### 6. Evaluation

The notebook calculates test-set classification accuracy and prints the learned decision rules using scikit-learn's `export_text()`.

### 7. Model Export

The trained classifier is saved as `methane_detection_model.pkl` when the relevant notebook cells execute successfully.

## Project Structure

```text
methane-detection/
├── README.md
└── methan-decision-tree.ipynb
```

The model file is generated during execution and is not necessarily included in the repository.

## Installation

```bash
pip install numpy pandas scikit-learn joblib jupyter
```

## How to Run

1. Clone or download the repository.
2. Obtain `ethylene_methane.txt`.
3. Update the dataset path in the notebook.
4. Install the dependencies.
5. Open `methan-decision-tree.ipynb` in Jupyter Notebook, JupyterLab, or Kaggle.
6. Execute the notebook cells in order.
7. Check the dataset structure, classification accuracy, and decision rules.
8. Verify that the trained model file is generated.

## Results

The notebook calculates classification accuracy and prints the learned decision rules. Actual numerical results should be added after running the model successfully.

## Limitations

- The classifier uses only three sensor features in the final modeling section.
- Binary classification does not estimate exact methane concentration.
- Dataset parsing and column alignment must be verified.
- Performance may vary under different sensor and environmental conditions.
- The notebook does not constitute a complete real-time gas monitoring system.

## Future Improvements

- Add precision, recall, F1-score, and a confusion matrix.
- Compare the Decision Tree with Random Forest and other models.
- Test on independent gas sensor measurements.
- Add sensor calibration and data-quality checks.
- Develop a real-time inference pipeline.
- Document the dataset source and dependency versions.

## Disclaimer

This project is intended for educational and research purposes. It is not a certified gas detector and must not replace calibrated methane monitoring equipment or industrial safety systems.
