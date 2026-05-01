# NFL Project Overview

This project analyzes whether regular-season NFL team performance metrics can explain and quantify team success (measured by wins). Using team level data from the 2015–2024 NFL seasons sourced from the nflverse R package, we examined which offensive and defensive metrics are most strongly associated with winning and how well they can explain season outcomes.

## Data & Features
- Seasons: 2015–2023 training, 2024 testing 
- Response variable: Team wins
- Key engineered features:
  - Offensive and defensive success rate
  - Offensive and defensive EPA per play
  - Point differential per game
  - Turnover differential

## Methodology

Due to strong multicollinearity between many football efficiency metrics, we fit an Elastic Net regression model, which combines L1 (Lasso) and L2 (Ridge) regularization. Hyperparameters were selected via cross-validation to minimize mean squared error. This approach allows correlated predictors to be shrunk together while reducing the influence of less informative variables.

## Results
<img width="828" height="578" alt="actual vs expected" src="https://github.com/user-attachments/assets/feb6c377-f7e9-4054-8a98-14132acdcf1e" />

Model performance on the 2024 season:

MAE: 1.22 wins  
RMSE: 1.46 wins  
R²: 0.84  

The model explains roughly 84% of the variation in team wins, with average prediction error just over one win. The most influential predictors were:

<img width="766" height="533" alt="FI_NFL_Model" src="https://github.com/user-attachments/assets/24bcd6f8-db10-4500-a6a4-b7fb9d1505b9" />


Most teams were predicted accurately, with a few notable outliers driven by close game variance and situational factors.

## Key Takeaways
- Team efficiency metrics are strongly associated with NFL success.
- Offensive and defensive consistency matters more than playcalling tendencies alone.
- Even strong models cannot fully account for randomness, injuries, coaching decisions, and game to game variance.

## Limitations & Future Work
- No true preseason or forward-looking predictive power
- Does not explicitly model injuries, weather, or coaching decisions
- Future extensions could include game-level modeling, Bayesian approaches, or incorporating roster and injury data


# Tommy John Project Overview

This project investigates the relationship between Tommy John surgery (ulnar collateral ligament injury) and pitcher pitch characteristics in Major League Baseball. Specifically, it examines whether velocity and spin rate across different pitch types are associated with an increased likelihood of undergoing Tommy John surgery.

The motivation behind this analysis is to better understand how modern pitching trends—such as increased velocity and spin—may relate to arm injuries. As pitchers continue to push physical limits, identifying statistical relationships between pitch metrics and injury history can provide insight for teams, analysts, and player development staff.

## Research Question

Are pitch velocity and spin rate associated with the occurrence of Tommy John surgery, and does this relationship differ by pitch type?

## Pitch characteristics examined in this project include:

- Fastball velocity
- Breaking ball velocity
- Off-speed pitch velocity
- Fastball spin rate
- Breaking ball spin rate
- Off-speed pitch spin rate

## Data Description

The dataset consists of MLB pitch-level tracking data aggregated to the pitcher–season level. Each observation represents a single pitcher in a given season and includes summary statistics for pitch velocity and spin rate by pitch category.

Pitchers were labeled based on Tommy John surgery status using publicly available injury and surgery records. This allowed for comparisons between pitchers who have undergone the procedure and those who have not.

## Pitch Classification

Individual pitch types were grouped into three broad categories:

Fastballs (e.g., four-seam, two-seam, sinkers)
Breaking balls (e.g., sliders, curveballs)
Off-speed pitches (e.g., changeups, splitters)

This grouping reduces noise from pitch-type granularity and allows for clearer interpretation of results.

## Data Sources

This project combines pitch-tracking and injury data from multiple public baseball analytics sources:

Baseball Savant – pitch-level Statcast data, including pitch velocity and spin rate
FanGraphs – supplemental pitching metrics and player information
ESPN – publicly reported injury and surgery histories used to identify Tommy John surgery

These sources were merged to create a pitcher–season level dataset containing both performance metrics and injury indicators.

## Data Preparation

Significant preprocessing was required to align pitch-tracking data with injury records across multiple data sources.

### Name Standardization and Merging

Player names appeared in inconsistent formats across datasets (e.g., "Last, First" vs. "First Last"). To ensure accurate joins:

Player names were normalized by:
Removing punctuation and whitespace
Converting all text to lowercase
Reformatting comma-separated names into a consistent structure
A cleaned name field was created in both the pitch data and injury data and used as the merge key.

### Pitch-level performance data were then merged with injury records using this standardized identifier.

- Injury Labeling
- Injury descriptions were scanned for mentions of “Tommy John” surgery.
- A binary indicator (HadTommyJohn) was created:
  - 1 if a pitcher had undergone Tommy John surgery 0 otherwise
- Missing injury records were treated as no documented Tommy John surgery.

### Feature Construction

Pitch-level data were aggregated to the pitcher–season level and grouped into three pitch categories:

- Fastballs
- Breaking balls
- Off-speed pitches

For each pitcher-season and pitch category, the following features were computed:

- Average pitch velocity
- Average spin rate
- Total pitch count (used for filtering reliability)

Only pitchers with sufficient pitch counts were retained to reduce noise from small samples.

### Final Dataset

The final modeling dataset includes:

- Pitcher name and season
- Pitch counts by pitch category
- Average velocity and spin rate for each pitch category
- Binary Tommy John surgery indicator

This cleaned and merged dataset forms the basis for all subsequent exploratory analysis and correlation modeling.

## Methodology

This analysis focuses on identifying associations, not causal relationships, between pitch characteristics and Tommy John surgery.

### Analytical Approach
- Correlation analysis was used to measure the strength and direction of the relationship between Tommy John surgery status and each velocity and spin rate metric.
- Correlations were evaluated separately for fastballs, breaking balls, and off-speed pitches to determine whether injury associations differ by pitch type.
- Exploratory visualizations (such as scatterplots and correlation matrices) were used to identify trends, outliers, and potential nonlinear patterns.
### Assumptions and Scope
- The analysis does not imply causation; higher velocity or spin rate does not necessarily cause injury.
- Injury timing, pitching workload, biomechanics, rest patterns, and prior injuries were not explicitly modeled.
- Tommy John surgery was treated as a static outcome rather than a time-to-event process.
