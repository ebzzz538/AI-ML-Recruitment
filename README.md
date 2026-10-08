# Student Academic Risk Prediction

This project uses student performance data to classify academic risk as Low, Medium or High. It explores the relationship between attendance and marks, trains a Decision Tree classifier and creates a CSV report with predictions and study recommendations.

## Dataset

[Student Dataset on Kaggle](https://www.kaggle.com/datasets/ganeshkumarofficial/student-dataset)

The supplied data has 10,030 rows. After removing 30 duplicate records, 10,000 students remain. Missing and invalid values are handled during cleaning; missing model inputs are filled with medians calculated from the training data.

## Method

1. Inspect and clean the dataset.
2. Plot attendance and score distributions and compare attendance with total marks.
3. Define risk groups from `Total_Score`:
   - **High:** below 60
   - **Medium:** 60 to below 75
   - **Low:** 75 and above
4. Train a Decision Tree using attendance, midterm marks, assignment marks, quiz marks and participation.
5. Evaluate on a separate 20% test set using accuracy, precision, recall, F1-score and a confusion matrix.
6. Generate a CSV with predicted risk and rule-based recommendations.

`Total_Score` is not used as an input to the model because it was used to define the risk groups. The cutoffs are project choices, not official grading rules.

## Results

| Metric | Result |
|---|---:|
| Accuracy | 50.15% |
| Weighted precision | 0.4245 |
| Weighted recall | 0.5015 |
| Weighted F1-score | 0.3449 |
| Attendance vs. total score correlation | -0.0109 |

The model correctly identified only **1 of the 391 High-risk students** in the test set. Its predictions are not reliable enough for real academic interventions. The results and confusion matrix are included in the notebook.

## Files

- `AI_ML_Student_Risk_Analysis.ipynb` — code, graphs, evaluation and prediction examples
- `student_risk_report.csv` — student labels, attendance, midterm marks, predicted risk and recommendations
- `README.md` — project overview and instructions

## Run

Open the notebook in Google Colab and select **Runtime → Run all**. Upload the original Kaggle ZIP or CSV when prompted. The last code cell saves `student_risk_report.csv`.
