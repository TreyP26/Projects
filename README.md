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

This project analyzes the correlation of a pitcher getting a Tommy John Injury to number of pitches, spin rate of pitcher's fast ball, spin rate of pitcher's breaking ball, spin rate of pithcer's off speed ball, velocity of pithcer's fastball, velocity of pitcher's breaking ball, and velocity of pithcer's off speed ball.  
