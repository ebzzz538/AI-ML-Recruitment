# Student Academic Risk Prediction — Ebi

## Objective and dataset
Analyze the supplied `studentkaggle.zip` / `dcs_student_data.csv`, explore attendance versus marks, and test classification into project-defined support bands. Original: **10,030 × 21**; after 30 duplicate removals: **10,000 unique records**.

## Files
| File | Purpose |
|---|---|
| AI_ML_Student_Risk_Analysis.ipynb | Actual notebook with Markdown explanations, Python code, executed outputs, 8 figures and evaluation. |
| student_risk_report.csv | 10,000 anonymous records with predictions, score-rule labels, recommendations and prediction provenance. |
| INTERVIEW_GUIDE.md | Detailed beginner explanations, actual results, 38 interview Q&As and short revision scripts. |
| PROJECT_SUMMARY.md | Concise submission/revision summary. |
| README.md | This overview and run instructions. |

## How to run
**Google Colab:** Upload/open `AI_ML_Student_Risk_Analysis.ipynb`, select **Runtime → Run all**, and upload the original ZIP when prompted. The last reporting cell writes and offers the CSV for download.

**Jupyter:** Put the original ZIP or its CSV beside the notebook and run all cells. Standard pandas, NumPy, Matplotlib, Seaborn and scikit-learn are required. The original ZIP is not embedded in the notebook. Saved outputs can be viewed without retraining; rerun the cells to recreate the fitted models in memory.

**Validation:** All 17 code cells executed sequentially against the original data, with outputs saved and 8 embedded charts inspected. Predictions, baselines, metrics and CSV integrity checks passed. Execution used Python with notebook output capture because this environment has no Jupyter kernel; the Colab interface itself was not tested here. Exact package versions are printed in the notebook.

## Risk, features and methods
Risk from Total_Score: **High <60; Medium 60–<75; Low ≥75**. These are illustrative support bands, not official university policy. Inputs: attendance, midterm, assignments, quizzes, participation and department. Outcomes, identifiers, unnecessary personal details and assessment fields with uncertain timing are excluded.

Training-only median imputation, scaling and one-hot encoding are in a Pipeline. Compare Logistic Regression, Decision Tree and Random Forest, plus majority and stratified DummyClassifiers. Select with 5-fold development macro F1, then evaluate on a reserved 20% test split. All randomness uses seed 42.

## Actual results
- Attendance/total Pearson correlation: **-0.0109**.
- Risk proportions: Low **50.10%**, Medium **30.35%**, High **19.55%**.
- Best learned classifier: **Random Forest**; CV macro F1 **0.3351** vs random baseline **0.3415**.
- Test accuracy **33.25%**; macro F1 **0.3165**; weighted F1 **0.3402**.
- High recall **25.58%**: 100/391 found, 291 missed.

## Conclusion
The selected ML model did not beat the stratified baseline on development macro F1 and is not reliable for operational intervention. Weak available signal is an honest result. The report distinguishes predicted labels from known score-rule bands; recommendations are separate explicit rules. Timing, provenance, generalization, fairness and probability calibration require further validation. Use human review, and use the direct score rule when final totals are already known.
