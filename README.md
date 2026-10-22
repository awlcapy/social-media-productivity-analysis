# social-media-productivity-analysis
How do social media, notifications, sleep, and stress affect student productivity? EDA + classification in Python.

# Social Media vs Productivity: EDA and Prediction

Which digital habits are linked to student productivity? This project explores a dataset of 30,000 student responses and builds classification models to predict whether a student is productive or less productive.

## Key Findings

- **Job satisfaction and sleep efficiency** show the strongest positive relationship with productivity.
- **Notification load and stress level** are the main negative factors.
- **Random Forest reached 89.97% accuracy**, slightly ahead of Logistic Regression (89.72%) on the test set.
- Engineered features (sleep efficiency, work-rest balance, burnout rate, digital stimulation) showed meaningful correlation with the target.

![Correlation heatmap](images/correlation-heatmap.png)

## Dataset

[Social Media vs Productivity](https://www.kaggle.com/datasets/mahdimashayekhi/social-media-vs-productivity) from Kaggle: 30,000 rows and 19 columns covering social media time, notification load, sleep, stress, work habits, and productivity scores.

The notebook downloads the dataset automatically with `kagglehub`, so the CSV does not need to be added manually.

## Methodology

1. **Collect and inspect data:** load the dataset, review structure and descriptive statistics.
2. **Validate:** check missing values (found in several key columns) and duplicates (none found).
3. **Select features:** keep 16 relevant variables.
4. **Clean:** fill missing numeric values with the median.
5. **Feature engineering:** create `sleep_efficiency`, `work_rest_balance`, `burnout_rate`, and `digital_stimulation_norm`.
6. **Label:** `is_productive` = 1 if `actual_productivity_score` is at or above the median, otherwise 0. The original score is removed from the features to prevent data leakage.
7. **Model:** 80/20 train-test split, Logistic Regression vs Random Forest (100 trees).
8. **Evaluate:** accuracy, confusion matrix, and classification report.

## Results

| Model | Accuracy |
|---|---|
| Logistic Regression | 89.72% |
| Random Forest | 89.97% |

Both models reach an F1-score of about 0.90. Random Forest was chosen as the final model for its consistency across both classes.

## Tech Stack

Python, Pandas, NumPy, Matplotlib, Seaborn, scikit-learn, kagglehub

## How to Run

```bash
git clone https://github.com/awlcapy/social-media-productivity-analysis.git
cd social-media-productivity-analysis
pip install pandas numpy matplotlib seaborn scikit-learn kagglehub
jupyter notebook
```

Open the notebook and run all cells. Kaggle notebook version: [link here](https://www.kaggle.com/code/salsabilaarfanaulia/social-media-vs-productivity-eda-and-prediction)

## Author

Salsabila Arfan Aulia | Software Engineering Technology, IPB University
[LinkedIn](https://linkedin.com/in/salsabila-arfan-aulia-909637342)
