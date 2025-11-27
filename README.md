# 🧠 MLOpsE2EClassificationTermProject

This project implements a complete **MLOps pipeline** for a **U.S. Visa Approval Classification System**, covering all essential components — from **data ingestion** to **deployment and monitoring**.
The goal is to predict whether a visa application will be approved or denied, using machine learning and production-grade MLOps tools.

---

## 📘 Overview

This project demonstrates:

* **Data ingestion & transformation**
* **Model training & hyperparameter optimization**
* **Model registry and versioning with AWS S3**
* **FastAPI deployment**
* **Continuous evaluation with Evidently AI**

It is designed following **end-to-end MLOps best practices**, ensuring scalability, reproducibility, and maintainability.

---

## ⚙️ Tech Stack

| Category               | Tools / Libraries                                                        |
| ---------------------- | ------------------------------------------------------------------------ |
| **Data Processing**    | pandas, numpy, matplotlib, seaborn, plotly                               |
| **ML Modeling**        | scikit-learn, xgboost, catboost, imblearn, scipy                         |
| **MLOps & Monitoring** | dill, PyYAML, neuro_mf, boto3, botocore, mypy-boto3-s3, evidently==0.2.8 |
| **Database**           | pymongo                                                                  |
| **Backend/API**        | fastapi, uvicorn, jinja2, python-multipart                               |
| **Utilities**          | from_root, certifi, dnspython                                            |

---

## 📂 Project Structure

```
MLOpsE2EClassificationTermProject/
│
├── data/                        # Raw & processed data
├── notebooks/                   # Exploratory analysis notebooks
├── src/
│   ├── components/              # Data ingestion, transformation, training modules
│   ├── pipeline/                # Training & prediction pipelines
│   ├── utils/                   # Helper functions
│   ├── logger.py                # Custom logging
│   ├── exception.py             # Error handling
│
├── app.py                       # FastAPI main application
├── template.py                  # Folder structure generator
├── requirements.txt
├── setup.py
└── README.md
```

---

## 🧩 Installation

### 1️⃣ Create and activate conda environment

```bash
conda create -n visa python=3.8 -y
conda activate visa
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ (If MongoDB error occurs)

```bash
pip uninstall -y pymongo motor mongoengine djongo
pip install -U "pymongo>=4.7" dnspython certifi
```

---

## 🧠 Features

### 🧮 Data Preprocessing

* Handles missing values and outliers
* Encodes categorical variables
* Normalizes numeric features

### 🧠 Model Training

* Trains multiple models (XGBoost, CatBoost, RandomForest, etc.)
* Uses **GridSearchCV** for parameter optimization
* Saves model artifacts with `dill`

### ☁️ Model Versioning & Storage

* Stores trained models and metadata in **AWS S3**
* Uses `boto3` and `neuro_mf` for version tracking

### ⚡ Deployment via FastAPI

* REST API endpoint for prediction: `/predict`
* Web UI using Jinja2 templates
* Deployed using **Uvicorn**

### 📊 Continuous Monitoring

* Integrated with **Evidently AI (v0.2.8)** for drift detection
* Tracks model performance and feature drift over time

---

## 🚀 Usage

### 🧪 Run training pipeline

```bash
python src/pipeline/training_pipeline.py
```

### ⚙️ Start API server

```bash
uvicorn app:app --reload
```

### 📈 Generate Evidently report

```bash
python src/components/data_monitoring.py
```

---

## 🧾 Example API Request

### POST `/predict`

```json
{
  "case_id": "A12345",
  "country_of_origin": "India",
  "education_level": "Masters",
  "job_experience": 5,
  "employer_size": 200,
  "prev_visa_denials": 0
}
```

**Response:**

```json
{
  "prediction": "Approved",
  "probability": 0.89
}
```

---

## ☁️ AWS Integration

### Environment Variables

Create a `.env` file in the root directory:

```
AWS_ACCESS_KEY_ID=<your_aws_key>
AWS_SECRET_ACCESS_KEY=<your_secret_key>
MONGODB_CLUSTER_URI=<your_mongo_connection_string>
BUCKET_NAME=<your_s3_bucket_name>
AWS_DEFAULT_REGION=<your_aws_region>
ECR_REPO=<your_ecr_url>
```

---

## 🧹 Troubleshooting

If you face MongoDB issues:

```bash
pip uninstall -y pymongo motor mongoengine djongo
pip install -U "pymongo>=4.7" dnspython certifi
```

If S3 upload fails:

* Check your **AWS credentials**
* Verify **IAM role permissions**
* Ensure **correct bucket region**

---

## 📊 MLOps Pipeline (Flow)

```
    A[Data Ingestion] --> B[Data Transformation]
    B --> C[Model Training]
    C --> D[Model Evaluation]
    D --> E[Model Storage (AWS S3)]
    E --> F[FastAPI Deployment]
    F --> G[Prediction API]
    G --> H[Monitoring (Evidently AI)]
    H --> A
```

---

## 📦 Requirements Summary

```
pandas
numpy
matplotlib
plotly
seaborn
scipy
scikit-learn
imblearn
xgboost
catboost
pymongo
from_root
evidently==0.2.8
dill
PyYAML
neuro_mf
boto3
mypy-boto3-s3
botocore
fastapi
uvicorn
jinja2
python-multipart
-e .
```

---

## 👨‍💻 Author

**Pankaj Kumar Pramanik**
Data, AI & MLOps Engineer
🌐 [pankajpramanik.com](https://pankajpramanik.com)


