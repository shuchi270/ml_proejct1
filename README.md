# End-to-End Machine Learning Project: Student Performance Prediction

This is an end-to-end Machine Learning project designed to predict a student's performance (math score or overall score) based on various demographic and socio-economic features. The project encompasses the complete ML lifecycle, from problem formulation and Exploratory Data Analysis to model serving using a Flask web application.

## 🚀 Project Overview

The core objective of this project is to build a predictive model that can estimate a student's performance based on their background information such as gender, race/ethnicity, parental level of education, lunch plan, test preparation course, reading score, and writing score.

## 📂 Project Structure

```text
├── artifacts/              # Directory to store outputs like data, models (model.pkl), and preprocessors (preprocessor.pkl)
├── logs/                   # Directory to store log files generated during execution
├── notebook/               # Jupyter notebooks for Exploratory Data Analysis (EDA) and Model Training experiments
├── src/                    # Source code for the project
│   ├── components/         # Core ML Pipeline steps
│   │   ├── data_ingestion.py        # Module for reading and splitting data
│   │   ├── data_transformation.py   # Module for feature engineering and preprocessing
│   │   └── model_trainer.py         # Module to train and evaluate various ML models
│   ├── pipeline/           # End-to-end execution pipelines
│   │   ├── predict_pipeline.py      # Pipeline for making predictions on new data
│   │   └── train_pipeline.py        # Pipeline for triggering the training process
│   ├── exception.py        # Custom exception handling script
│   ├── logger.py           # Custom logging script
│   └── utils.py            # Utility functions used across the project (e.g. saving/loading objects)
├── templates/              # HTML templates for the Flask web application
│   ├── index.html          # Landing page
│   └── home.html           # Prediction input form and results page
├── app.py                  # Flask web application entry point
├── requirements.txt        # Required python packages for the project
├── setup.py                # Script to build the project as a python package
└── README.md               # Project documentation
```

## 🔄 Machine Learning Pipeline Flow

The project follows a structured modular pipeline approach:

1. **Data Ingestion (`data_ingestion.py`)**: 
   - Reads the raw dataset.
   - Splits the dataset into train and test sets.
   - Saves the split datasets into the `artifacts/` folder.

2. **Data Transformation (`data_transformation.py`)**: 
   - Handles missing values.
   - Applies encoding for categorical variables (e.g., One-Hot Encoding).
   - Scales numerical features (e.g., StandardScaler).
   - Saves the transformation logic as a `preprocessor.pkl` file for future use.

3. **Model Training (`model_trainer.py`)**: 
   - Trains multiple Machine Learning models (e.g., Random Forest, Decision Tree, Gradient Boosting, Linear Regression, etc.).
   - Evaluates models using appropriate metrics (e.g., R2 Score).
   - Selects the best performing model.
   - Saves the final model as `model.pkl`.

4. **Prediction Pipeline (`predict_pipeline.py`)**: 
   - Loads the saved `preprocessor.pkl` and `model.pkl`.
   - Takes new real-time inputs.
   - Applies the transformation and predicts the outcome.

## 🌐 Web Application

A Flask-based web application (`app.py`) is provided to offer a user-friendly interface for the model:
- **`GET /`**: Renders the welcome/index page.
- **`GET /predictdata`**: Renders the form to input student details.
- **`POST /predictdata`**: Receives the form data, passes it through the prediction pipeline, and displays the prediction result on the web page.

## 🛠️ Setup & Installation

Follow these steps to set up the project on your local machine:

1. **Clone the repository:**
   ```bash
   git clone <your-repository-url>
   cd end2end_project
   ```

2. **Create a virtual environment (optional but recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Flask application:**
   ```bash
   python app.py
   ```
   The application will be accessible at `http://0.0.0.0:5000/` or `http://localhost:5000/`.

## ⚙️ Tecstack

- **Programming Language**: Python 3
- **Web Framework**: Flask
- **Data Manipulation & Analysis**: Pandas, NumPy
- **Machine Learning**: Scikit-Learn, CatBoost, XGBoost
- **Frontend**: HTML, CSS 
