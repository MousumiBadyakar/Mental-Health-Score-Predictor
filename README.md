# 🧠 Mental Health Score Predictor

An end-to-end Machine Learning application that predicts a student's mental health score (0–10) based on their social media usage patterns, academic activities, lifestyle habits, and perceived stress level.

The project combines a **Machine Learning regression pipeline**, a **FastAPI backend**, and an interactive web interface to provide real-time predictions through a simple and intuitive experience.

## 🚀 Live Demo

| Resource | Link |
|---|---|
| 🌐 Live Application | [Mental Health Score Predictor](https://mental-health-score-predictor-1-n1kg.onrender.com) |
| 📘 API Documentation | [Swagger UI](https://mental-health-score-predictor-intm.onrender.com/docs) |

## ✨ Features

- **Mental Health Score Prediction:** Predicts a numerical mental health score between 0 and 10 using a trained Random Forest regression model.
- **Lifestyle Analysis:** Considers sleep duration, physical activity, study hours, and perceived stress.
- **Social Media Insights:** Uses daily screen time, phone unlock frequency, most-used platform, and primary usage purpose.
- **Interactive Dashboard:** Provides a clean, responsive interface with an animated score gauge.
- **REST API Integration:** Connects the frontend to a FastAPI backend for real-time predictions.
- **Input Validation:** Implements client-side validation and Pydantic-based backend validation.
- **Swagger Documentation:** Provides interactive API documentation for testing endpoints.
- **Cloud Deployment:** Deployed using Render.

## 🖥️ Application Preview

The application collects student information through three sections:

1. **Profile:** Age, gender, and country.
2. **Academic & Digital Habits:** Academic level, social media platform, usage purpose, daily screen time, and phone unlocks.
3. **Lifestyle & Stress:** Study hours, physical activity, sleep duration, and perceived stress level.

After submission, the application displays the predicted mental health score with a visual gauge and an indicative score category.

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Data Analysis | Pandas, NumPy |
| Data Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| ML Algorithm | Random Forest Regressor, Linear Regression |
| Backend | FastAPI |
| Data Validation | Pydantic |
| Model Serialization | Joblib |
| Frontend | HTML, CSS, JavaScript |
| API Communication | REST API, Fetch API |
| Deployment | Render |

## 📊 Dataset

**Dataset:** `Student_Social_Media_And_Mental_Health_Impact.csv`

The dataset contains information about **5,000 students** with 13 columns, including demographic information, social media habits, lifestyle factors, and the target variable.

### Input Features

| Feature | Description |
|---|---|
| Age | Student's age |
| Gender | Gender |
| Country | Country of residence |
| Academic_Level | High School, Undergraduate, or Graduate |
| Most_Used_Platform | Most frequently used social media platform |
| Purpose_Of_Use | Primary purpose of social media usage |
| Avg_Daily_Usage_Hours | Average daily social media usage |
| Daily_Unlocks | Number of daily phone unlocks |
| Study_Hours | Daily study duration |
| Physical_Activity_Hours | Daily physical activity duration |
| Sleep_Hours_Per_Night | Average nightly sleep duration |
| Stress_Level | Perceived stress level |

**Target Variable:** `Mental_Health_Score` (continuous numerical value).

## ⚙️ Machine Learning Workflow

The project follows a complete supervised learning regression workflow.

1. **Exploratory Data Analysis (EDA)**
   - Dataset inspection and statistical analysis.
   - Distribution analysis of the target variable.
   - Correlation analysis and visualization.
   - Analysis of stress, screen time, and sleep patterns.

2. **Data Cleaning**
   - Checked missing values and duplicate records.
   - Handled invalid negative physical activity values.
   - Examined outliers and feature distributions.

3. **Feature Engineering**
   - Grouped countries based on their frequency.
   - Retained the most frequent countries and categorized the remaining countries as `Other`.

4. **Data Preprocessing**
   - Used `SimpleImputer` for missing-value handling.
   - Applied `log1p` transformation to skewed study-hour data.
   - Applied scaling to numerical features.
   - Used Ordinal Encoding for stress levels.
   - Used One-Hot Encoding for nominal categorical features.
   - Implemented preprocessing through `ColumnTransformer`.

5. **Model Training**
   - Linear Regression as the baseline model.
   - Random Forest Regressor for capturing nonlinear relationships.
   - Hyperparameter tuning using `RandomizedSearchCV`.

6. **Model Evaluation**
   - R² Score
   - Mean Absolute Error (MAE)
   - Root Mean Squared Error (RMSE)

7. **Model Deployment**
   - Saved the trained preprocessing and prediction pipeline using Joblib.
   - Integrated the model with FastAPI.
   - Connected the frontend to the prediction endpoint.

## 📈 Model Performance

The following results were obtained from the 70:30 train-test split.

| Model | Training R² | Testing R² | MAE | RMSE |
|---|---:|---:|---:|---:|
| Linear Regression | 0.7237 | 0.7398 | 0.5362 | 0.6760 |
| Random Forest (Default) | 0.9809 | **0.8780** | **0.3465** | **0.4629** |
| Random Forest (Tuned) | 0.9547 | 0.8652 | 0.3687 | 0.4865 |

**Selected Model:** Random Forest Regressor (Default)

The default Random Forest model achieved an R² score of approximately **87.80%** on the test dataset.

*Note: These metrics represent model performance on the dataset and do not establish clinical validity.*

## 🏗️ Project Architecture

```text
Mental-Health-Score-Predictor/
│
├── main.py
│   └── FastAPI backend and prediction endpoint
│
├── index.html
│   └── Frontend structure
│
├── style.css
│   └── Application styling
│
├── script.js
│   └── Form validation and API integration
│
├── Mental_Health_Model.pkl
│   └── Trained ML pipeline
│
├── Mental_Health_Predictor.ipynb
│   └── EDA, preprocessing, model training
│       and evaluation
│
├── Student_Social_Media_And_Mental_Health_Impact.csv
│   └── Dataset
│
├── requirements.txt
│   └── Python dependencies
│
└── .gitignore
```

## 🔌 API Documentation

The backend is developed using FastAPI and exposes a REST endpoint for generating predictions.

**Base URL:**

```text
https://mental-health-score-predictor-intm.onrender.com
```

### Available Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Welcome endpoint |
| POST | `/predict` | Predicts the mental health score |

### Prediction Request

**Endpoint:**

```http
POST /predict
```

**Sample JSON Request:**

```json
{
  "age": 22,
  "gender": "Female",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Entertainment",
  "avg_daily_usage_hours": 5.5,
  "daily_unlocks": 75,
  "study_hours": 6,
  "physical_activity_hours": 1,
  "sleep_hours_per_night": 7,
  "stress_level": "Medium"
}
```

**Sample JSON Response:**

```json
{
  "predicted_mental_health_score": 7.25
}
```

*The response value above is an illustrative example.*

Explore and test the API through the [Interactive Swagger Documentation](https://mental-health-score-predictor-intm.onrender.com/docs).

## 💻 Run Locally

Follow these steps to run the project on your local machine.

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Mental-Health-Score-Predictor
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI Backend

```bash
uvicorn main:app --reload
```

The API will be available at:

```text
http://127.0.0.1:8000
```

### 5. Open the Frontend

Open `index.html` in your browser to access the application.

Make sure the frontend API base URL in `script.js` points to your locally running backend:

```javascript
const API_BASE = "http://127.0.0.1:8000";
```

## ☁️ Deployment

The application is deployed on **Render** with separate frontend and backend services.

- **Frontend:** Hosts the interactive HTML, CSS, and JavaScript application.
- **Backend:** Hosts the FastAPI application and serves predictions using the trained ML pipeline.
- **API Documentation:** Automatically generated using FastAPI's Swagger UI.

## ⚠️ Disclaimer

This application is developed for educational and informational purposes only.

The predicted score is based on patterns learned from the dataset and should not be interpreted as a medical diagnosis, psychological evaluation, or substitute for professional mental health advice.

## 👩‍💻 Author

**Mousumi Badyakar**

---

⭐ If you find this project interesting, consider giving the repository a star!
