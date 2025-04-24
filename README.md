FlareGuard - Wildfire Risk Assessment Using Supervised Machine Learning
This repository hosts a Flask-based web application that performs probabilistic wildfire risk prediction using a trained supervised machine learning model. The solution integrates real-time meteorological data via the Weatherstack API and applies a classification pipeline to determine the likelihood of wildfire occurrences in a given geographic location.

Project Overview
The model leverages key environmental variables—namely ambient temperature (°C), relative humidity (%), wind speed (km/h), and precipitation (mm)—as predictive features to estimate fire risk levels. These inputs are passed through a pre-trained classification algorithm (e.g., Random Forest or Gradient Boosting, stored in model.pkl) which outputs the posterior probability of wildfire risk. The model was trained on labeled environmental datasets, wherein each observation was annotated with a binary class representing fire occurrence (1) or non-occurrence (0).

Supervised Learning Pipeline
The pipeline involves:

Data preprocessing (normalization, missing value imputation)

Feature engineering (selection of the most influential meteorological variables)

Model training and tuning (hyperparameter optimization using cross-validation)

Evaluation using metrics such as ROC-AUC, precision-recall, and F1-score

The final model was serialized using pickle and is dynamically loaded at runtime within the Flask server context for scalable inference.

API Integration and Application Flow
User inputs a location.

Real-time weather data is fetched using HTTP GET requests to the Weatherstack API.

Data is parsed, cleaned, and mapped to model-compatible features.

The model predicts the fire risk as a probability score.

Based on predefined thresholds, the app classifies the risk into:

Low (<50%)

Moderate (50-75%)

High (>75%)

Risk messages and weather conditions are rendered via Flask’s flash() and render_template() mechanisms.

Security and Robustness
Includes exception handling for API errors, model prediction errors, and network failures.

Uses os.urandom() for securely generating Flask secret keys.

Prevents unauthorized access through basic input sanitation and structured error feedback.

This project exemplifies the application of supervised learning models in a real-time decision support system for environmental hazard prediction.
