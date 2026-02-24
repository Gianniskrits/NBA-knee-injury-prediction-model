Predicting Severe Knee Injuries in NBA Players 

Author:
Ioannis Kritsotakis (University of Patras, Department of Electrical and Computer Engineering) 

Project Overview:
Basketball players face a high risk of injury due to repetitive musculoskeletal stresses from pivoting, jumping, and rapid direction changes. Knee injuries are among the most common and severe injuries in professional basketball.The objective of this project is to predict the absolute risk (probability) of a player suffering a season-ending severe knee injury based on their in-game performance statistics.

Data Sources & Processing:
The project utilizes a combination of two datasets sourced from Kaggle covering the 2010-2011 through 2019-2020 NBA seasons:
Injury Dataset: Scraped from Pro Sports Transactions, filtered for keywords like "knee" and "meniscus," and coded for severity (e.g., "out for season" or "out indefinitely").
In-Game Statistics Dataset: Scraped from basketball-reference.com, featuring continuous predictors like minutes played, shot attempts, rebounds, and fouls.
After substantial data cleaning, standardizing team names, and linking the datasets, the final dataset contained 5,010 player records. Of these records, 234 (4.7%) represented season-ending knee injuries.This data set is included in this repository. Note that the data cleaning process was not done in python so it isnt included in the project.
The pre-processed data sets can be found on kaggle using the links: 
nab-injuries 2010-2020: https://www.kaggle.com/datasets/ghopkins/nba-injuries-2010-2018
nba stats 2010-2020: https://www.kaggle.com/datasets/chrisgabriel/nba-stats-20102020
 
Methodology:
This project followed a 7-step framework for developing valid clinical prediction models.Language & Tools: Python-> scikit-learn, pandas, numpy, matplotlib, and seaborn.
Algorithm: Logistic Regression was used to predict the binary outcome of severe knee injury. The model converts log-odds into probabilities using a sigmoid function:
P = 1/{1 + e^(-z)} (Where z is the linear combination of predictor variables) 
Handling Multicollinearity:A correlation matrix was used to identify highly correlated predictors. To prevent inflated coefficient variance and overfitting, collinear variables like defensive rebounds, offensive rebounds, and total field goal attempts were dropped from the final model.

Model Performance:
The model's performance was evaluated based on both discriminatory ability and calibration.
Apparent Performance: The model achieved an Area Under the Curve (AUC) of 0.73. This means that if you randomly select one injured player and one healthy player, the model correctly assigns a higher risk to the injured player 73% of the time. Overall calibration was excellent with an observed-to-expected ratio of O/E = 1.
Internal Validation: To ensure the model generalizes to unseen data, a stratified 10-fold cross-validation was applied. The cross-validated AUC was 0.70, showing only a slight and expected drop in performance.

Example Application:
To demonstrate practical use, the model was applied to two Point Guards during the 2019-2020 season.
LeBron James (Remained healthy): The model predicted a 6.7% probability of severe knee injury.
Kyrie Irving (Suffered an injury): The model predicted a 43.5% probability of severe knee injury.

Future Directions:
While the current model is sufficiently accurate to be useful, future iterations could improve predictive power by:
Adding physiological predictors such as player height, weight, and Body Mass Index (BMI).
Improving the modeling of non-linear features (e.g., minutes played per game) using polynomial terms.
Addressing the non-independence of data points (multiple season records for the same player).

How to Run This Project:
Clone this repository to your local machine.Ensure you have Python installed, then install the required dependencies:
pip install -r requirements.txt
Run the Jupyter Notebook model.ipynb to view the data processing, model training, and visualizations.

License:
This project is licensed under the Apache License 2.0 - see the LICENSE file for details.
