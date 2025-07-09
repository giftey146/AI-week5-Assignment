# AI-week5-Assignment
Part 1:Short Answers

1. Problem Definition (6 points)
Hypothetical AI Problem: Predicting student dropout rates in higher education institutions
3 Objectives:

Identify at-risk students early (by end of first semester) to enable timely intervention
Achieve 85% accuracy in predicting dropout likelihood within the first academic year
Reduce overall dropout rates by 20% through targeted support programs

2 Stakeholders:

Academic advisors and student support services - need early warning system to prioritize intervention efforts
University administration - require insights for resource allocation and retention strategy planning

1 Key Performance Indicator (KPI):
Reduction in actual dropout rate compared to baseline (measured as percentage decrease in students who leave within two years)
2. Data Collection & Preprocessing (8 points)
2 Data Sources:

Student Information System (SIS) - academic records, grades, course enrollment, attendance data
Learning Management System (LMS) - digital engagement metrics, assignment submissions, forum participation, time spent on coursework

1 Potential Bias:
Socioeconomic bias - Students from lower-income backgrounds may have less access to technology, affecting their digital engagement metrics in the LMS. This could lead the model to unfairly predict higher dropout risk for financially disadvantaged students based on technical limitations rather than academic capability.
3 Preprocessing Steps:

Handling missing data - Use median imputation for numerical features (GPA, test scores) and mode imputation for categorical features (major, enrollment status)
Feature normalization - Apply standardization to continuous variables like GPA, credit hours, and engagement metrics to ensure equal weight in model training
Temporal feature engineering - Create rolling averages and trend indicators for academic performance over time to capture learning trajectory patterns

3. Model Development (8 points)
Model Choice: Random Forest
Justification: Random Forest is ideal for this problem because it handles mixed data types well (numerical grades, categorical majors), provides feature importance rankings to identify key dropout predictors, is relatively interpretable for stakeholders, and is robust to outliers and missing data common in educational datasets.
Data Splitting Strategy:

Training set (70%): Used to train the model
Validation set (15%): Used for hyperparameter tuning and model selection
Test set (15%): Used for final, unbiased performance evaluation
Ensure temporal splitting (older cohorts for training, recent cohorts for testing) to simulate real-world deployment conditions

2 Hyperparameters to Tune:

Number of trees (n_estimators) - Affects model performance and computational cost; more trees generally improve accuracy but increase training time
Maximum depth (max_depth) - Controls overfitting; deeper trees may capture more complex patterns but risk memorizing training data rather than generalizing

4. Evaluation & Deployment (8 points)
2 Evaluation Metrics:

Recall (Sensitivity) - Critical because failing to identify an at-risk student who actually drops out is more costly than false alarms; we want to catch as many true dropouts as possible
Precision - Important to avoid overwhelming advisors with false positives; helps ensure intervention resources are used efficiently on students who truly need support

Concept Drift:
Concept drift occurs when the underlying relationship between input features and dropout likelihood changes over time. For example, economic conditions, curriculum changes, or generational differences in learning styles could alter what factors predict dropout.
Monitoring approach: Track model performance metrics monthly, compare feature distributions between training and current data, and retrain quarterly using recent data while maintaining performance benchmarks.
1 Technical Challenge:
Scalability - As the system expands to multiple universities with different academic systems, the model must handle varying data formats, different grading scales, and diverse institutional contexts while maintaining consistent performance across institutions with different student populations and academic structures
