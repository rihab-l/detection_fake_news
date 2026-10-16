# Fake News Detection using Machine Learning

## Overview

This project aims to automatically classify news articles as either **Fake News** or **Real News** using Natural Language Processing (NLP) and Machine Learning techniques.

The project includes data preprocessing, exploratory data analysis (EDA), feature extraction using TF-IDF, training and evaluation of multiple machine learning models, model comparison, and model persistence for deployment.

---

## Dataset

The project uses the **ISOT Fake News Dataset**, which contains:

- Fake news articles (`Fake.csv`)
- Real news articles (`True.csv`)

Each article includes:

- Title
- Text
- Subject
- Date

After preprocessing, the dataset is balanced and prepared for binary classification:

- 0 → Fake News
- 1 → Real News

---

## Project Workflow

### 1. Data Loading

- Import Fake and Real news datasets
- Explore dataset dimensions and structure

### 2. Data Preparation

- Add class labels
- Remove duplicates
- Merge datasets
- Shuffle observations
- Create a manual testing subset

### 3. Exploratory Data Analysis (EDA)

- Class distribution analysis
- Word clouds
- Subject distribution
- Text length distribution
- Dataset quality assessment

### 4. Text Preprocessing

The preprocessing pipeline includes:

- Lowercase conversion
- URL removal
- HTML tag removal
- Punctuation removal
- Stopword removal
- Tokenization
- Lemmatization

### 5. Feature Extraction

Text data is transformed into numerical vectors using:

- TF-IDF Vectorization
- Unigrams and Bigrams
- Maximum vocabulary size control

### 6. Model Training

The following machine learning models were trained and evaluated:

1. Multinomial Naive Bayes
2. XGBoost Classifier
3. SGD Classifier
4. Support Vector Machine (Linear SVC)
5. Decision Tree
6. Random Forest
7. Logistic Regression

### 7. Model Evaluation

Performance evaluation includes:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- ROC-AUC Score
- Cross Validation

### 8. Model Comparison

A complete comparison of all trained models is performed to identify the best-performing classifier.

### 9. Manual Testing

A separate set of articles is used for manual validation and performance verification.

### 10. Model Persistence

Trained models and TF-IDF vectorizers are saved using Joblib for future deployment.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- NLTK
- Scikit-Learn
- XGBoost
- WordCloud
- Joblib

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/fake-news-detection.git
cd fake-news-detection
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Notebook

Open Jupyter Notebook:

```bash
jupyter notebook
```

Then run:

```text
fake_news_detection_completed77.ipynb
```

---

## Saved Models

The notebook exports:

```text
models/
│
├── tfidf_vectorizer.pkl
├── logistic_regression.pkl
├── random_forest.pkl
├── svm.pkl
├── decision_tree.pkl
├── xgboost.pkl
├── naive_bayes.pkl
└── sgd_classifier.pkl
```

---

## Results

The project compares seven different machine learning algorithms for fake news classification.

The evaluation demonstrates that linear models combined with TF-IDF features achieve excellent performance on the ISOT Fake News Dataset.

---

## Future Improvements

- Deep Learning models (LSTM, GRU)
- Transformer-based models (BERT, RoBERTa)
- Real-time news verification API
- Web application deployment using Flask or Streamlit
- Multilingual fake news detection

---

## Author

Academic Machine Learning and NLP Project

Developed as part of a Data Science and Artificial Intelligence learning project.

---

## License

This project is intended for educational and academic purposes.
