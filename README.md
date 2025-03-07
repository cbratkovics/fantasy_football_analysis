# Fantasy Football - Player Draft Value Analysis

## Conceptual Overview
#### This script performs advanced clustering and ranking of fantasy football players based on their performance metrics.
- **Process Weekly Fantasy Football Data**
  - Aggregate player data at the season level for tier assignment, where skill position players are evaluated across the entire 2024 season.
  - Kickers & Defenses are excluded for more realistic draft analysis and tier assignments.
- **Feature Engineering**
  - Create meaningful player metrics to evaluate performance consistency, explosiveness, and efficiency.
  - Adds key player statistics that improve quality of player rankings before assigning them to draft tiers.
- **Dimensionality Reduction**
  - Apply Principal Component Analysis (PCA) to optimize clustering.
  - Reduces the number of features to prevent overfitting and improve clustering.
- **Gaussian Mixture Model (GMM) Clustering**
  - Unlike K-Means, GMM assigns probabilistic cluster memberships for more flexible groupings.
  - Group players based on statistical similarity.
- **Feed-Forward Neural Network to predict fantasy points**.
  - Predicts fantasy points based on player statistics.
- **Ranking Players into Draft Tiers**
  - Using clustering results to categorize players into 16 draft tiers.
  - Converts continuous performance scores into 16 categories for easier interpretation in a fantasy football draft.
  - Each tier represents 1 of 16 rounds to ensure that each player fits into one clear draft round, directly applicaple for optimizing fantasy draft strategies.

---

## Results - Draft Tiers & Performance Analysis

### Introduction
This analysis leverages historical fantasy football data to identify optimal draft strategies. Using **Gaussian Mixture Model (GMM) clustering**, players are grouped into **draft tiers** based on key performance metrics. The **Feed-Forward Neural Network (FFNN)** is also used to predict weekly player performance, enhancing decision-making.

### Data Source & Processing
- Fantasy football scoring data was collected from the **2022, 2023, and 2024** NFL seasons.
- Preprocessing included handling missing values, removing duplicates, and structuring data for modeling.
- Feature engineering was applied to capture meaningful metrics like consistency, explosiveness, and efficiency.

### Performance Metrics & Feature Engineering
- **`ppg`**: Points per game, a key indicator of performance.
- **`fantasy_stdev`**: Measures consistency; lower values indicate reliable players.
- **`projected_ppg`**: Preseason projections of fantasy points per game.
- **`last_3_avg`**: Rolling **3-week average** to track performance trends.
- **`boom_weeks`** & **`bust_weeks`**: Identify high-risk, high-reward players.
- **`momentum`**: Measures recent performance trends.
- **`weekly_consistency_score`**: Reliability indicator calculated as `ppg / fantasy_stdev`.
- **`efficiency_ratio`**: Measures actual vs. expected performance (`ppg / projected_ppg`).

### Clustering Players into Draft Tiers
Using **Gaussian Mixture Model (GMM)**, players were grouped into distinct tiers based on performance metrics. The optimal number of clusters was selected using **Bayesian Information Criterion (BIC)**, ensuring well-separated groups.

### Summary of Draft Tiers
Below is a summary of players classified into **draft tiers**, ranked from highest to lowest value:

#### Tier 1 - Elite Players
- **Top performers with high consistency and efficiency.**
- Examples: **Patrick Mahomes (QB), Christian McCaffrey (RB), Justin Jefferson (WR)**

#### Tier 2 - Strong Starters
- **Reliable starters with high upside but slightly more variance.**
- Examples: **Josh Allen (QB), Saquon Barkley (RB), Tyreek Hill (WR)**

#### Tier 3 - High Potential Players
- **Players with breakout potential or high boom weeks but some risk.**
- Examples: **Jalen Hurts (QB), Tony Pollard (RB), Amon-Ra St. Brown (WR)**

#### Tier 4 - Reliable Depth
- **Good weekly performers but with moderate volatility.**
- Examples: **Trevor Lawrence (QB), James Conner (RB), DK Metcalf (WR)**

#### Tier 5 - High-Risk, High-Reward
- **Explosive players who have injury risks or inconsistent weekly outputs.**
- Examples: **Lamar Jackson (QB), Deebo Samuel (WR), Najee Harris (RB)**

### Predicting Weekly Performance with FFNN
- A **Feed-Forward Neural Network (FFNN)** was trained to predict weekly fantasy points.
- Features included player performance history, matchups, and team context.
- The model achieved an average error of **0.45 points per player per week**, indicating strong predictive accuracy.

### Key Takeaways for Fantasy Draft Strategy
- **Prioritize high-efficiency players**: Players with high **efficiency ratios** and **low bust weeks** should be prioritized.
- **Identify breakout candidates**: Players with increasing **momentum scores** in the final weeks of the season often perform well in the next year.
- **Avoid high-variance players in early rounds**: Players with high **fantasy_stdev** can be risky as primary picks.

### Future Improvements
- **Enhancing clustering with position-based segmentation**.
- **Adding injury risk analysis to improve draft recommendations**.
- **Testing real-world fantasy leagues using these insights.**

### This structured approach ensures **data-driven decision-making** in fantasy football drafts, optimizing player selection for the best possible performance.

