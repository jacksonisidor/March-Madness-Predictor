# March Madness Predictor

This repository contains a comprehensive data science project that utilizes historical college basketball data to simulate March Madness brackets.

## Goal
The primary objectives of this data science project are:
- Predict individual college basketball matchups
- Identify potential upsets
- Make a prediction for the 2024 March Madness bracket

It's called "March Madness" for a reason. The tournament is known for being particularly unpredictable in the past, with no one ever coming close to a perfect bracket. With this in mind, I wanted to combine my knowledge of statistics, data, and basketball to beat the odds. Due to the winner-take-all aspect each matchup, a perfect bracket is practically impossible, so hopefully I can at least tame the madness enough to give me an edge over the average person.

## Data Sources
The original data files utilized in this project are sourced from Nishaan Amin on Kaggle, specifically "Tournament Matchups.csv" containing information on who played against who, and "KenPom Barttorvik.csv" containing tons of valuable team statistics that I will use to evaluate the matchups. 

## Simulator Results
To maximize standard bracket scoring, I implemented the scoring metric using by ESPN, CBS, NCAA, etc. that doubles the point value for correct scores each round. 
Over the range of our available data, the average user score was 67, while the average seed-based bracket score is 88, indicating that simply picking the higher seed does significantly better than the average person. However, my simulator achieved an average of 98, out-performing both. If you remove the unpredictable outlier of a year that 2023 was, this score easily surpasses 100, with many years scoring well into the 130's.

To be exact, 8 of the 14 years scored over 109, 5 over 120, and 3 beat 130. While exact user data is not fully public, this simulator would place comfortably high on the leaderboard almost every year. Because of the inherent unpredicability of March Madness, there is a wide range of scores in my model testing, but when compared to the field, it consistently performs better than 99% of users. 

## Project Structure
#### MM Data Folder
  - Original Data Sets From Kaggle: 
    - `KenPom Barttorvik 2024.csv`: Team statistics for all 2024 tournament teams sourced from https://kenpom.com/ and https://www.barttorvik.com/#
    - `KenPom Barttorvik.csv`: Team statistics for all 2008-2023 tournament teams sourced from https://kenpom.com/ and https://www.barttorvik.com/#
    - `Tournament Matchups 2024.csv`: The first round matchups for 2024 March Madness
    - `Tournament Matchups.csv`: All matchups from March Madness tournaments 2008-2023 (excluding 2020 for COVID)
  - Processed Data Sets
    - `raw_stats.csv`: Raw (unranked) stats from the most correlated variables to "round" (how far the team made it in the tournament)
    - `matchup_stats.csv`: Cleaned and processed matchup data with raw stats included for all the teams (this is what is used in the predictions/simulations)

#### Data Processing Folder:
  - `kenpom_processing.ipynb`: The notebook outlining the processing of the team stats data mentioned above
  - `matchups_processing.ipynb`: The notebook cleaning/processing matchup data and appropriately merging with team stats

#### Predictions Folder
  - `single_matchup_SVM_predictor.ipynb`: The optimization of an SVM model that predicts the winner of single matchups between two teams using various statistcs
  - `single_matchup_XGB_predictor.ipynb`: The optimization of an XGBoost model that predicts the winner of single matchups between two teams using various statistcs
  - `full_bracket_simulator.ipynb`: Optimizing a full bracket simulator (rather than single matchups) using custom simulation pipelines and scoring metrics
  - `MM2024Simulation.ipynb`: Training the optimized simulator on all available historical data to predict the 2024 March Madness bracket (results coming soon)


