IST 664: Natural Language Processing

**Project:** Email Spam Classifier — Enron Email Spam Corpus
**Student:** Najah Bell
**Tools:** Python · scikit-learn · NLTK · pandas · Logistic Regression · Feature Engineering



Project Overview

This project built a machine learning pipeline to classify emails as spam or ham (not spam) using the Enron Email Spam Corpus. Multiple feature engineering experiments were implemented and evaluated using 5-fold cross-validation to identify the most effective combination of features for spam detection.



Dataset

•	**Source:** Enron Email Spam Corpus
•	**Task:** Binary classification — spam vs. ham
•	**Evaluation:** 5-fold cross-validation across all feature experiments



Feature Experiments

Five feature sets were implemented and compared:

| Experiment | Features Used |
|------------|--------------|
| Unigrams | Individual word tokens |
| Bigrams | Two-word sequences |
| POS Tags | Part-of-speech tag distributions |
| Stylometric Features | Email length, punctuation density, capitalization rate, special character usage |
| Logistic Regression | Combined feature set with LR classifier |



Model & Results

**Classifier:** Logistic Regression
**Evaluation Method:** 5-fold cross-validation

Each feature experiment was evaluated independently to measure the contribution of different linguistic signals to spam classification accuracy. The stylometric features captured writing style patterns unique to spam emails — such as excessive capitalization, punctuation, and special characters — that unigram and bigram models alone may miss.



Deliverables

•	Python classification script implementing all 5 feature experiments
•	Code Walkthrough document explaining the implementation



Files in This Folder

| File | Description |
|------|-------------|
| spam_classifier.ipyb | Full classification pipeline with all feature experiments |
| IST664_Presentation.pdf | Project presentation slides (if available) |



Reflection

This project demonstrated that feature engineering choices have a significant impact on classifier performance in NLP tasks. Stylometric features — capturing how an email is written rather than just what words it contains — added a dimension of signal that bag-of-words approaches miss entirely. The use of 5-fold cross-validation ensured that performance estimates were robust and not dependent on a single train/test split, reflecting best practices for evaluating text classification models.
