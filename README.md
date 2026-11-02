# LifeWell XAI: Life Satisfaction Prediction System

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)

A machine learning web app that predicts whether a person is satisfied with their life using only **seven survey inputs**. The app shows the prediction instantly and explains which factors matter most through a feature importance analysis.

**Course:** CSE 299 (Junior Design Project), North South University
**Supervisor:** [Mr. Intisar Tahmid Naheen]

## Overview

Life satisfaction surveys are usually long, which reduces participation and slows large-scale analysis. LifeWell XAI reduces the burden by selecting a small set of strong predictors from a large census survey, then training and comparing several classifiers. The best model is deployed in a simple Streamlit interface with dark mode.

## Key Features

- **Minimal input:** only 7 questions (age plus six survey indicators)
- **Multi-model comparison:** Logistic Regression, KNN, Naive Bayes, SVM, Gradient Boosting, XGBoost, and BART
- **Explainability:** feature importance chart shows which inputs influence the prediction most
- **Real-time prediction** through a web interface
- **Dark mode** for comfortable use

## Input Features

| Code | Feature |
|------|---------|
| age | Age |
| A2 | General health |
| B1 | Financial satisfaction |
| C1 | Stress level |
| D1 | Housing satisfaction |
| E1 | Social support |
| G1 | Community engagement |

## Dataset

SHILD2012 Census survey: 18,957 records with 384 columns covering demographics, health, life satisfaction, and socio-economic conditions. Preprocessing included handling missing values, one-hot encoding of categorical variables, and a train/test split. See the report for full details.

## Methodology

1. Data cleaning and preprocessing
2. Feature selection down to 7 predictors
3. Training multiple supervised models and a transformer-based model (BART)
4. Evaluation using Accuracy, Precision, Recall, and F1-score
5. Deploying the Gradient Boosting model (`gb_model_7features.pkl`) in a Streamlit app

## Results

The deployed Gradient Boosting model reached an accuracy of **0.9334** and an F1-score of **0.9300** on the test set. The full model comparison, confusion matrices, and discussion are in the [project report](docs/LifeWell_XAI_report.pdf).

## Demo

Watch the demo video: [`docs/demo.mp4`](docs/2025-12-19 22-58-49.mp)

## Project Structure

```
LIFEWELL_XAI/
├── README.md
├── requirements.txt
├── .gitignore
├── src/
│   ├── app.py                         Streamlit web app
│   ├── gb_model_7features.pkl         Trained Gradient Boosting model
│   └── LifeWell_XAI.ipynb             Training and evaluation notebook
└── docs/
    ├── LifeWell_XAI_report.pdf        Project report
    ├── LifeWell_XAI_presentation.pptx Presentation slides
    └── demo.mp4                       App demo video
```

## Run Locally

```bash
git clone https://github.com/<your-username>/LIFEWELL_XAI.git
cd LIFEWELL_XAI
pip install -r requirements.txt
cd src
streamlit run app.py
```

The app opens at `http://localhost:8501`. Run it from inside the `src` folder so it can find the model file.

## Tech Stack

Python, scikit-learn, XGBoost, Hugging Face Transformers (BART), Pandas, NumPy, Streamlit, Google Colab

## Team

- MD Fahim Hossain Khan
- Ahmad Abdullah Sifat
- Poner Hossain Piyal
- Smrity Akter Ful

North South University, Dhaka, Bangladesh

## Limitations

- The model predicts from survey responses and is not a clinical or diagnostic tool.
- Results depend on the SHILD2012 dataset and may not generalize to other populations.

