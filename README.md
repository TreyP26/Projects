# Data Science & Sports Analytics Projects

This repository contains a collection of data science and statistical modeling projects focused on sports analytics, regression modeling, and exploratory data analysis. Each project includes a detailed methodology, analysis, and discussion of results.

## Projects
### 🏈 NFL Team Success Modeling

Goal: Identify which team performance metrics are most strongly associated with NFL regular-season success.

- Data from 2015–2024 NFL seasons
- Team-level efficiency metrics (EPA, success rate, turnover differential, point differential)
- Elastic Net regression to handle multicollinearity
- Model explains ~84% of variation in team wins

📄 Full project description:
➡️ nfl-team-success.md

### ⚾ Tommy John Injury & Pitch Characteristics

Goal: Examine the relationship between pitch velocity/spin rate and Tommy John surgery incidence among MLB pitchers.

- Pitch-level Statcast data aggregated to pitcher–season level
- Velocity and spin rate analyzed across fastballs, breaking balls, and off-speed pitches
- Injury data merged from public sources
- Focuses on correlation, not causation

📄 Full project description:
➡️ tommy-john-pitch-metrics.md

## Tools & Technologies
- Languages: R, Python
- Libraries: pandas, numpy, scikit-learn, nflverse, ggplot2

## Methods:
- Elastic Net regression
- Correlation analysis
- Feature engineering
- Data cleaning & merging
- Exploratory Data visualization
Notes
These projects emphasize interpretability and statistical reasoning over black-box prediction.
All analyses are based on publicly available data.
Results should be interpreted as descriptive associations rather than causal claims.
