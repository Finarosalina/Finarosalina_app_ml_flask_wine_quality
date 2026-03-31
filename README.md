# 🍷 Wine Quality Predictor — Flask ML Deployment

**End-to-end machine learning deployment: KNN classifier served via a Flask web app, deployed on Render.**

**[🚀 Live app on Render](https://flask-render-integration-uuog.onrender.com)**

---

## Overview

This project takes the KNN wine quality classifier built in [Finarosalina_KNN_BUENO_ML_WINE](https://github.com/Finarosalina/Finarosalina_KNN_BUENO_ML_WINE) and deploys it as a production web application using Flask and Render.

Users enter 11 physicochemical wine features through a web form and receive an instant prediction of wine quality (low / medium / high) powered by the pre-trained KNN model.

---

## Architecture

```
User (browser)
     │
     ▼
Flask Web App (app.py)
     │
     ├── HTML Form (templates/index.html)   ← input features
     ├── StandardScaler (scaler.pkl)        ← preprocessing
     └── KNN Model (knn_model.pkl)          ← prediction
     │
     ▼
Render (cloud deployment)
```

---

## Features

- Web form with 11 input fields for physicochemical wine parameters
- Real-time prediction with user-friendly result display
- Responsive design (mobile-friendly)
- Example values provided in the UI to guide users
- Model and scaler loaded from pre-trained `.pkl` files
- Deployed and publicly accessible via Render

---

## Input Features

| Feature | Description |
|---|---|
| Volatile acidity | Acetic acid level |
| Citric acid | Freshness and flavor |
| Residual sugar | Sugar remaining after fermentation |
| Chlorides | Salt content |
| Free SO₂ | Free sulfur dioxide |
| Total SO₂ | Total sulfur dioxide |
| Density | Density of the wine |
| pH | Acidity level |
| Sulphates | Sulphate additive |
| Flavanoids | Phenolic compounds |
| Alcohol | Alcohol percentage |

---

## Output

| Prediction | Meaning |
|---|---|
| 0 | Low quality wine |
| 1 | Medium quality wine |
| 2 | High quality wine |

---

## Tech Stack

- **Backend** — Python, Flask
- **ML** — scikit-learn (KNN), joblib
- **Frontend** — HTML, CSS (Jinja2 templates)
- **Deployment** — Render (cloud platform)
- **Model source** — [KNN Wine Quality project](https://github.com/Finarosalina/Finarosalina_KNN_BUENO_ML_WINE)

---

## Project Structure

```
Finarosalina_app_ml_flask/
├── app.py                  # Flask application
├── models/
│   ├── knn_model.pkl       # Pre-trained KNN classifier
│   └── scaler.pkl          # Fitted StandardScaler
├── templates/
│   └── index.html          # Web form and result display
├── requirements.txt
└── README.md
```

---

## How to Run Locally

```bash
# Clone the repository
git clone https://github.com/Finarosalina/Finarosalina_app_ml_flask.git
cd Finarosalina_app_ml_flask

# Install dependencies
pip install flask scikit-learn joblib pandas numpy requests

# Run the app
python app.py
```

Then open `http://localhost:5000` in your browser.

---

## Deployment on Render

This app is deployed on [Render](https://render.com) as a web service. The app listens on the port provided by the environment variable `PORT`, making it compatible with Render's infrastructure out of the box.

```python
port = int(os.environ.get("PORT", 5000))
app.run(host="0.0.0.0", port=port)
```

---

## Key Learnings

- Serving a pre-trained scikit-learn model via Flask is straightforward but requires careful scaler/model versioning — both must be fitted on the same data
- Render provides a simple and free deployment path for Flask apps with automatic builds from GitHub
- Loading the model from a remote URL at startup (requests + joblib) is a clean way to decouple model storage from application code
- HTML forms with Jinja2 templating allow rapid prototyping of ML-powered interfaces without a frontend framework

---

## Related Projects

- [🍷 KNN Wine Quality Classifier](https://github.com/Finarosalina/Finarosalina_KNN_BUENO_ML_WINE) — model training and optimization
- [🔗 URL Spam Detection (NLP)](https://github.com/Finarosalina/Finarosalina_NLP_DL) — NLP pipeline with SVM
- [🌍 Air Quality & Mortality](https://github.com/ullaom/air-quality-politics) — Random Forest with Streamlit deployment

---

*Part of the 4Geeks Academy Data Science & ML program portfolio.*
