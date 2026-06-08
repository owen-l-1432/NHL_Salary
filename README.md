#NHL Player Salary Prediction
**Project Overview**

This project predicts NHL player salaries using a Random Forest regression model built in R. The goal is to identify which on-ice performance metrics most strongly drive player compensation, and to build a model that generalizes well to unseen players.

Dataset

The dataset contains NHL player statistics and salary information, including:
On-ice performance metrics: points, goals, time on ice, plus-minus, takeaways, giveaways, hits, penalty minutes
Player attributes: age, nationality, team, position
Injury data: games injured

Tools Used

R (randomForest, ranger, caret, moments),
RMarkdown


**Methodology**

Preprocessing

Log-transformed right-skewed predictors (pts, goal, age, takeaway, giveaway, pim, hits) after checking skewness distributions
Converted categorical variables (nationality, team, position) to integer encodings
Applied 2nd-degree polynomial transformations to games played and plus-minus based on their nonlinear relationships with salary

Feature Engineering

Created 10 interaction terms capturing meaningful relationships between performance metrics:
pts_toi, goal_toi, take_toi, give_toi, pm_toi (performance × ice time)
toi_gp, toi_inj, toi_age (ice time × usage/context)
pim_hits (physical play interaction)
injure_pts (injury impact on production)

Modeling

Trained a Random Forest model using the ranger package via caret
Used 5-fold cross-validation with a grid search across 50 hyperparameter combinations to optimize model performance
Evaluated feature importance using permutation-based variable importance

**Key Findings**

Points, goals, and time on ice were the strongest predictors of NHL player salary, suggesting teams most heavily reward consistent offensive production and ice time deployment
Interaction terms between performance metrics and time on ice meaningfully improved model accuracy, indicating that production per minute of deployment matters beyond raw counting stats
Final model achieved an RMSLE of 0.30868 on the holdout test set

Files:
code_file.Rmd — Full analysis with preprocessing, feature engineering, model building, and evaluation
report.pdf — Rendered PDF report
