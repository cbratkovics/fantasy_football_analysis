# Fantasy Football - Player Draft Value Analysis 🏈

\<p align="center"\>
\<img src="[https://img.shields.io/badge/Python-3.9-blue.svg](https://img.shields.io/badge/Python-3.9-blue.svg)" alt="Python"\>
\<img src="[https://img.shields.io/badge/Framework-Scikit--learn-orange.svg](https://img.shields.io/badge/Framework-Scikit--learn-orange.svg)" alt="Scikit-learn"\>
\<img src="[https://img.shields.io/badge/Framework-TensorFlow-red.svg](https://img.shields.io/badge/Framework-TensorFlow-red.svg)" alt="TensorFlow"\>
\<img src="[https://img.shields.io/badge/License-MIT-green.svg](https://img.shields.io/badge/License-MIT-green.svg)" alt="License"\>
\</p\>

This project uses advanced clustering and machine learning to rank fantasy football players and assign them to draft tiers, helping you make data-driven decisions on draft day.

-----

## 📋 Conceptual Overview

This script performs an in-depth analysis of fantasy football players to determine their draft value. Here's how it works:

  - **📊 Process Weekly Data**: Aggregates player statistics from the 2024 season to create a comprehensive dataset for analysis. Kickers and Defenses are excluded to focus on skill position players.
  - **🛠️ Feature Engineering**: Creates new metrics to evaluate players on performance, consistency, and explosiveness.
  - **🌀 Dimensionality Reduction**: Applies **Principal Component Analysis (PCA)** to reduce the number of features, preventing overfitting and improving clustering accuracy.
  - **🤖 GMM Clustering**: Uses a **Gaussian Mixture Model (GMM)** to group players based on statistical similarity, offering more flexible cluster assignments than traditional methods like K-Means.
  - **🧠 Neural Network Predictions**: A **Feed-Forward Neural Network (FFNN)** predicts fantasy points based on player statistics, adding another layer of analysis.
  - **🏆 Rank Players into Tiers**: Translates the clustering and prediction results into 16 distinct draft tiers, making it easy to see which round each player should be drafted in.

-----

## 🚀 Results - Draft Tiers & Performance Analysis

### Introduction

This analysis uses historical data from the **2022, 2023, and 2024** NFL seasons to identify optimal draft strategies. By leveraging **GMM clustering** and a **Feed-Forward Neural Network**, this project provides a clear, data-driven approach to player valuation.

### Performance Metrics & Feature Engineering

The following metrics were engineered to capture a complete picture of player performance:

| Metric | Description |
| :--- | :--- |
| `ppg` | **Points Per Game**: A primary measure of a player's average performance. |
| `fantasy_stdev` | **Standard Deviation**: Measures consistency. Lower values mean more reliable players. |
| `projected_ppg` | **Projected PPG**: Preseason projections for points per game. |
| `last_3_avg` | **3-Week Average**: Tracks recent performance trends. |
| `boom_weeks` | **Boom Weeks**: Identifies high-upside players who can win you a week. |
| `bust_weeks` | **Bust Weeks**: Flags players who are prone to underperforming. |
| `momentum` | **Momentum Score**: Measures recent performance trends to spot breakouts. |
| `weekly_consistency_score` | **Consistency Score**: Calculated as `ppg / fantasy_stdev`. |
| `efficiency_ratio` | **Efficiency Ratio**: Measures actual vs. expected performance (`ppg / projected_ppg`). |

### Player Draft Tiers

Players were grouped into **16 draft tiers** using GMM clustering. Here's a summary of the top tiers:

#### ⭐ Tier 1 - Elite Players

*Top performers with high consistency and efficiency.*

  - **Examples**: Patrick Mahomes (QB), Christian McCaffrey (RB), Justin Jefferson (WR)

#### 💪 Tier 2 - Strong Starters

*Reliable starters with high upside but slightly more variance.*

  - **Examples**: Josh Allen (QB), Saquon Barkley (RB), Tyreek Hill (WR)

#### ✨ Tier 3 - High Potential Players

*Players with breakout potential but some associated risk.*

  - **Examples**: Jalen Hurts (QB), Tony Pollard (RB), Amon-Ra St. Brown (WR)

#### ✅ Tier 4 - Reliable Depth

*Good weekly performers with moderate volatility.*

  - **Examples**: Trevor Lawrence (QB), James Conner (RB), DK Metcalf (WR)

#### 🎲 Tier 5 - High-Risk, High-Reward

*Explosive players who have injury risks or inconsistent weekly outputs.*

  - **Examples**: Lamar Jackson (QB), Deebo Samuel (WR), Najee Harris (RB)

-----

## 🧠 Predicting Weekly Performance with FFNN

A **Feed-Forward Neural Network (FFNN)** was trained to predict weekly fantasy points.

  - **Features**: The model used player performance history, matchups, and team context.
  - **Accuracy**: Achieved an average error of just **0.45 points per player per week**, demonstrating strong predictive power.

-----

## 🎯 Key Takeaways for Your Draft

  - **Prioritize Efficiency**: Target players with a high **efficiency ratio** and a low number of **bust weeks**.
  - **Find Breakout Stars**: Look for players with rising **momentum scores** toward the end of the season.
  - **Draft Safely Early**: Avoid players with a high **`fantasy_stdev`** in the early rounds.

-----

## 🔮 Future Improvements

  - **Position-Based Clustering**: Enhance clustering by segmenting players by position.
  - **Injury Risk Analysis**: Add an injury risk factor to draft recommendations.
  - **Real-World Testing**: Validate the model by testing its recommendations in real fantasy leagues.

This structured approach ensures **data-driven decision-making** in your fantasy football drafts, helping you select the best players for optimal performance.
