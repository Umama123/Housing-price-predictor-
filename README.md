# Housing-price-predictor
Predict housing price index using a machine learning model (Polynomial Ridge Regression) with a Django web interface and deployment via Hugging Face and ngrok
# 🏠 Housing Price Index Predictor (ML + Django)

This project predicts the **House Price Index (HPI)** using a **Polynomial Ridge Regression** model trained on macroeconomic indicators. It features a web UI built with **Django** and deployed through **Hugging Face** and **ngrok**.


##  Table of Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [1. Dataset & Preprocessing](#1-dataset--preprocessing)
- [2. Model Training](#2-model-training)
- [3. Model Deployment (Hugging Face)](#3-model-deployment-hugging-face)
- [4. Web UI using Django](#4-web-ui-using-django)
- [5. Live Web App](#5-live-web-app)
- [6. How to Run Locally](#6-how-to-run-locally)
- [7. File Structure](#7-file-structure)
- [8. Dependencies](#8-dependencies)
- [9. Author](#9-author)



##  Project Overview

 **Goal**: Predict House Price Index (HPI) based on 8 macroeconomic features.
  **Model**: Polynomial Ridge Regression with SGD and early stopping.
 **Tools**: Google Colab, Hugging Face, Django, pyngrok



## Tech Stack

| Component       | Technology         |
|----------------|--------------------|
| Model Training | `scikit-learn`     |
| Data Handling  | `pandas`, `numpy`  |
| Web UI         | `Django`           |
| Deployment     | `Hugging Face`, `ngrok`, `Google Colab` |

---

## 1. Dataset & Preprocessing

- Dataset: `global_housing_market_extended.csv`
- Target variable: `House Price Index`
- Features used:
  - GDP Growth
  - Inflation Rate
  - Mortgage Rate
  - Unemployment Rate
  - Urbanization Rate
  - Population Growth
  - Construction Index
  - Rent Index
- Preprocessing:
  - Removed non-numeric columns (`Country`, `Year`)
  - Applied `StandardScaler` on both input and target
  - Generated PolynomialFeatures (degree=2)

---

## 2. Model Training

- Model: `Ridge` (L2 regularization) using `SGDRegressor`
- Enabled `early_stopping=True` to avoid overfitting
- Saved the following components using `pickle`:
  - Trained model
  - Scaler for X (`StandardScaler`)
  - Scaler for y
  - Polynomial transformer

---

## 3. Model Deployment (Hugging Face)

- Uploaded model components to  Hugging Face:
  - `ridge_model.pkl`
  - `scaler_X.pkl`
  - `scaler_y.pkl`
  - `poly_transformer.pkl`

**Model Repository**: [View on Hugging Face](https://huggingface.co/Umama927/Global-Housing-Market-Analysis)

---

## 4. Web UI using Django

- Created a Django project (`housing_project`)
- Built a single app `predictor`
- UI Form (`index.html`) allows users to input 8 features
- Backend loads the Hugging Face model and serves predictions
- View logic:
  - Preprocess → transform → predict → inverse scale → return result

---

## 5. Live Web App

Deployed Django UI using `ngrok` in Google Colab

 

