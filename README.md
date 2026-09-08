# CareerOS 🚀

AI-powered career readiness and skill-gap analysis platform that evaluates a user's skills against a target career role and generates a personalized learning roadmap.

## Overview

CareerOS helps users answer a simple question:

> **"How ready am I for the career I want, and what should I learn next?"**

The system takes a user's current skill profile and desired career role, analyzes the gap between required and existing skills, predicts a career-readiness score using a machine learning model, and generates a personalized roadmap.

## Key Features

- 🎯 Career-role based skill analysis
- 🔍 Skill gap detection
- 🤖 Machine-learning based readiness prediction
- 📊 Career readiness percentage
- 🧭 Personalized weekly learning roadmap
- 📚 Learning-resource recommendations
- 💼 Career-level classification
- 💰 Readiness-based salary estimation
- 📈 Role-specific skill demand analysis
- 🌐 FastAPI REST API
- 📖 Interactive Swagger API documentation

## System Architecture

```text
                 User Skill Profile
                         │
                         ▼
                  Target Career Role
                         │
                         ▼
               ┌─────────────────────┐
               │   Skill Gap Engine  │
               └──────────┬──────────┘
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
       Coverage Ratio            Average Skill
                                  Weight
              │                       │
              └───────────┬───────────┘
                          ▼
                ┌──────────────────┐
                │ ML Readiness     │
                │ Prediction Model │
                └─────────┬────────┘
                          │
                          ▼
                  Readiness Score
                          │
          ┌───────────────┼────────────────┐
          ▼               ▼                ▼
     Missing Skills    Roadmap          Salary
          │               │                │
          ▼               ▼                ▼
      Resources     Weekly Plan      Salary Band

Machine Learning

CareerOS currently uses a Linear Regression model from scikit-learn to estimate career readiness.

Model Inputs

The current model uses two features:

coverage_ratio — proportion of required role skills the user has
avg_weight — average importance/strength of the matched skills
Model Output

The model predicts:

Readiness Score (%)

The model is trained using training_data.csv and saved as:

Backend/edu_navigator/readiness_model.pkl
Model Evaluation

The current implementation evaluates the model using:

R² Score
Mean Squared Error (MSE)

Note: the current training dataset is synthetic. Therefore, the evaluation metrics measure performance on the generated dataset and should not be interpreted as real-world hiring or interview prediction accuracy.

Supported Career Roles

CareerOS currently supports roles including:

ML Engineer
Data Analyst
Data Scientist
Backend Developer
Full Stack Developer
AI Engineer
Cloud Engineer
Business Analyst
NLP Engineer
Front End Developer
Example Request
Endpoint
POST /analyze
Request Body
{
  "user_skills": {
    "Python": 0.8,
    "SQL": 0.6,
    "TensorFlow": 0.5,
    "PyTorch": 0.4,
    "Scikit-Learn": 0.7,
    "Docker": 0.3
  },
  "target_role": "ML Engineer"
}
Example Response
{
  "readiness_percent": "10.7%",
  "confidence_score": 14.63,
  "career_level": "Beginner",
  "progress_color": "red",
  "top_missing_skills": [
    "Kubernetes",
    "Feature Engineering",
    "Model Deployment"
  ],
  "weekly_roadmap": {
    "Week 1": "Kubernetes",
    "Week 2": "Feature Engineering",
    "Week 3": "Model Deployment",
    "Week 4": "CI/CD"
  },
  "estimated_salary_band": "3-5 LPA (Entry Level)"
}
Project Structure
CareerOS/
│
├── Backend/
│   ├── app.py
│   ├── requirements.txt
│   │
│   └── edu_navigator/
│       ├── __init__.py
│       ├── gap_engine.py
│       ├── generate_data.py
│       ├── predict.py
│       ├── readiness_model.pkl
│       ├── roadmap_engine.py
│       ├── salary_engine.py
│       ├── skill_data.py
│       ├── train_model.py
│       ├── training_data.csv
│       └── trend_engine.py
│
├── Frontend/
│
├── .gitignore
└── README.md
Getting Started
1. Clone the repository
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd CareerOS
2. Create a virtual environment
python -m venv venv
3. Activate the environment
Windows
venv\Scripts\activate
macOS / Linux
source venv/bin/activate
4. Install dependencies
pip install -r Backend/requirements.txt
5. Start the FastAPI server
cd Backend
uvicorn app:app --reload

The API will be available at:

http://127.0.0.1:8000

Swagger API documentation:

http://127.0.0.1:8000/docs
Current Technology Stack
Backend
Python
FastAPI
Pydantic
Machine Learning
scikit-learn
NumPy
Pandas
Joblib
API Documentation
Swagger / OpenAPI
Future Improvements

CareerOS is being developed toward a more complete AI-driven career intelligence platform.

Planned improvements include:

Resume parsing and automatic skill extraction
Real-world job-market data
Job-description skill frequency analysis
More meaningful career-readiness features
Improved ML models and model comparison
Personalized career recommendations
Real-time market trends
Better salary prediction using real-world data
Interview-readiness prediction
Frontend dashboard
Model monitoring and evaluation

Disclaimer

Career-readiness and salary estimates are intended for educational and career-planning purposes and should not be considered guaranteed employment or compensation predictions.
