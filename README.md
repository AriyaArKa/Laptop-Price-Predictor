﻿# Laptop Price Predictor

## Overview
The **Laptop Price Predictor** is a machine learning-based web application designed to predict laptop prices based on user-specified configurations. Developed using Python, Streamlit, and scikit-learn, this project processes a dataset of laptop specifications to train regression models for accurate price predictions. The application is deployed on Render and can be accessed [here](https://laptop-price-predictor-d0vi.onrender.com).

## Features
- **User-Friendly Interface**: Input laptop specifications like brand, type, RAM, weight, touchscreen, IPS display, screen size, resolution, CPU, HDD, SSD, GPU, and OS through an intuitive Streamlit interface.
- **Instant Predictions**: Get real-time price predictions based on user inputs.
- **Comprehensive Preprocessing**: Includes feature engineering such as PPI calculation, memory parsing, and categorical encoding.
- **Robust Model**: Utilizes a Voting Regressor combining multiple models for optimal performance.

## Dataset
The dataset (`laptop_data.csv`) includes laptop specifications and prices with the following features:
- **Columns**: Company, TypeName, Inches, ScreenResolution, CPU, RAM, Memory, GPU, OpSys, Weight, Price.
- **Preprocessing**:
  - Dropped irrelevant columns (e.g., `Unnamed: 0`).
  - Converted `RAM` and `Weight` to numeric values.
  - Extracted `Touchscreen` and `IPS` from `ScreenResolution`.
  - Calculated PPI from resolution and screen size.
  - Parsed `Memory` to extract HDD, SSD, Hybrid, and Flash Storage.
  - Simplified CPU and GPU brands into categories.
  - Grouped operating systems into Windows, Mac, and Others/No OS/Linux.

## Model Development
Multiple regression models were evaluated on log-transformed prices. The models tested include:

1. **Linear Regression**: R² = 0.81, MAE = 0.21
2. **Ridge Regression**: R² = 0.82, MAE = 0.20
3. **Lasso Regression**: R² = 0.81, MAE = 0.21
4. **K-Nearest Neighbors**: R² = 0.79, MAE = 0.22
5. **Decision Tree**: R² = 0.83, MAE = 0.19
6. **SVM**: R² = 0.80, MAE = 0.21
7. **Random Forest**: R² = 0.88, MAE = 0.16
8. **Extra Trees**: R² = 0.87, MAE = 0.17
9. **AdaBoost**: R² = 0.78, MAE = 0.23
10. **Gradient Boosting**: R² = 0.86, MAE = 0.17
11. **XGBoost**: R² = 0.87, MAE = 0.16
12. **Voting Regressor**: Combines Random Forest, Gradient Boosting, XGBoost, and Extra Trees (weights [5,1,1,1]). **Best Performance**: R² = 0.89, MAE = 0.16
13. **Stacking Regressor**: Uses Random Forest, Gradient Boosting, and XGBoost with Ridge as the final estimator. R² = 0.88, MAE = 0.16

### Selected Model
The **Voting Regressor** was chosen for its superior performance, achieving an **R² score of 0.89** and **MAE of 0.16** on the test set. It combines Random Forest, Gradient Boosting, XGBoost, and Extra Trees for robust predictions.

## Dependencies
- Python 3.8+
- streamlit
- scikit-learn
- pandas
- numpy
- matplotlib
- seaborn
- xgboost
- pickle

Install dependencies using:
```bash
pip install -r requirements.txt
```

## Project Structure
```
laptop-price-predictor/
├── laptop_data.csv       # Dataset
├── df.pkl                # Preprocessed DataFrame
├── pipe.pkl              # Trained Voting Regressor model
├── app.py                # Streamlit application
├── requirements.txt      # Dependencies
└── README.md             # Project documentation
```

## Running Locally
1. Clone the repository:
   ```bash
   git clone https://github.com/AriyaArKa/laptop-price-predictor.git
   cd laptop-price-predictor
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Streamlit app:
   ```bash
   streamlit run app.py
   ```
4. Access the app at `http://localhost:8501`.

## Deployment
The application is deployed on Render at [https://laptop-price-predictor-d0vi.onrender.com](https://laptop-price-predictor-d0vi.onrender.com). It runs in a Python environment with all required dependencies.

## Usage
1. Visit the deployed app or run it locally.
2. Select laptop specifications using dropdowns, sliders, and input fields.
3. Click **Predict Price** to see the estimated price for the configuration.

## Future Enhancements
- Add features like battery life or CPU generation for more granular predictions.
- Improve UI with visualizations of feature importance.
- Experiment with advanced hyperparameter tuning or new ensemble methods.
- Enable dynamic dataset updates for real-time accuracy.

## Contributors
- **Arka** ([AriyaArKa](https://github.com/AriyaArKa)) - Project lead, data preprocessing, model development, and deployment.

## License
This project is licensed under the MIT License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Acknowledgments
- Thanks to the open-source community for tools like Streamlit, scikit-learn, and xgboost.
- Dataset sourced from [provide source if applicable].
