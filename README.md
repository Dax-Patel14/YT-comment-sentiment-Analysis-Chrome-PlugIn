YT-comment-sentiment-Analysis-Chrome-PlugIn
==============================

# YouTube Sentiment Analyzer: Influencer Insights Platform

This project is a full-stack, production-ready system that enables influencers to analyze YouTube video comments using AI-powered sentiment analysis. It integrates a Chrome Extension frontend with a Flask backend and a modular ML pipeline, all wrapped with robust MLOps practices.

---

## 🚀 Project Overview

### Goal

To help content creators and marketing teams extract insights from YouTube comments in real time — including:

* Sentiment prediction (positive, neutral, negative)
* Sentiment trend over time
* Word cloud of top keywords
* Comment analytics (unique users, length, sentiment score)

---

## 🧱 Architecture

### 📦 Backend

* **Framework**: Flask
* **Model Serving**: MLflow Model Registry
* **Preprocessing**: NLTK-based cleaner + TF-IDF vectorizer
* **Model**: LightGBM trained with ADASYN-balanced data
* **Visualization**: Matplotlib + WordCloud

### 🧠 Machine Learning Pipeline

* Managed using **DVC**
* Stages:

  1. Data Ingestion
  2. Data Preprocessing
  3. Model Building (TF-IDF + LGBM)
  4. Model Evaluation
  5. Model Registration

### 🌐 Frontend (Chrome Extension)

* **Languages**: HTML, CSS, JavaScript
* **Files**:

  * `manifest.json`
  * `popup.html`
  * `popup.js`
* **Functionality**:

  * Extracts video ID from active tab
  * Uses YouTube API to fetch comments
  * Sends data to backend Flask API
  * Displays: sentiment pie chart, word cloud, trend graph, top comments

### 🔁 CI/CD Workflow

* **Tool**: GitHub Actions
* **Steps**:

  * Run ML pipeline (`dvc repro`)
  * Push artifacts to DVC remote (S3)
  * Test model loading, signature, and performance
  * Promote model in MLflow
  * Build and push Docker image to AWS ECR
  * Deploy via AWS CodeDeploy

---

## 📦 Deployment

### Backend

* Hosted on **AWS EC2**
* Uses **Docker + Gunicorn**
* Accessed at: `http://my-elb-357235934.us-east-1.elb.amazonaws.com`

### Chrome Extension

* Load manually from `chrome-extension/` folder via `chrome://extensions`
* Ensure Flask server is running before using

---

## 📂 Directory Structure

Project OrganizationAdd commentMore actions
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io
```

---

## 🧪 Testing

### Run Tests

```bash
pytest scripts/test_load_model.py
pytest scripts/test_model_signature.py
pytest scripts/test_model_performance.py
```

---

## 🛠️ Setup Instructions

### Prerequisites

* Python 3.10+
* Node.js + Chrome (for extension testing)
* AWS CLI configured
* YouTube Data API Key

### Clone Repo

```bash
git clone https://github.com/your-username/youtube-sentiment-analyzer.git
cd youtube-sentiment-analyzer
```

### Setup Backend

```bash
pip install -r requirements.txt
python app.py
```

### Launch Chrome Extension

1. Go to `chrome://extensions/`
2. Enable Developer Mode
3. Click "Load unpacked"
4. Select the `chrome-extension/` folder

---

## 📈 Key Metrics Tracked

* Accuracy, F1 Score, Precision, Recall
* Average sentiment score (normalized 0–10)
* Comment volume & length
* Sentiment trends by month
* Sentiment Distribution (Positive, Negative, Neutral)

---

## 🙌 Acknowledgements

* [YouTube Data API](https://developers.google.com/youtube/v3)
* [MLflow](https://mlflow.org/)
* [DVC](https://dvc.org/)
* [LightGBM](https://lightgbm.readthedocs.io/)
* [WordCloud](https://github.com/amueller/word_cloud)

---

## 📬 Contact

**Author:** Dax Patel
**Email:** [dakshpatel731@gmail.com](mailto:dakshpatel731@gmail.com)
**LinkedIn:** [linkedin.com/in/daxpatel]((https://www.linkedin.com/in/dax-patel14/))

---

## 🏁 Final Notes

> This project showcases an end-to-end AI solution with a Chrome plugin frontend, a modular MLOps backend, and a CI/CD system for continual model delivery — all designed to empower digital creators with real-time, intelligent insights from their audiences.





--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
