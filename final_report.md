# DSA210 Term Project: Steam Game Popularity Analysis

Student: Tuna Gürkan Uca  
Course: DSA 210 – Introduction to Data Science  
Term: Spring 2025-2026

---

## 1. Introduction

### 1.1 Motivation

The video game industry has grown rapidly, and thousands of games are released on platforms such as Steam. However, not every game reaches the same level of popularity. Some games attract millions of players, while others remain relatively unnoticed.

This project focuses on understanding which factors may influence the popularity of Steam games. Since I am interested in game development, analyzing what kinds of games attract larger player bases is useful for understanding player behavior and market trends.

In this project, estimated downloads are used as a proxy for game popularity. The analysis investigates whether variables such as price, genre, and review score are related to the number of estimated downloads.

---

### 1.2 Objectives

The main objectives of this project are:

* To collect and merge Steam game datasets from public sources
* To explore the distribution of game popularity using EDA
* To analyze the relationship between game features and estimated downloads
* To test hypotheses about price, genre, review score, and downloads
* To apply machine learning models to examine whether popularity can be predicted from simple features
* To identify limitations and possible future improvements

---

## 2. Data and Methodology

### 2.1 Data Sources

This project uses two publicly available Steam-related datasets from Kaggle.

#### Main Steam Dataset

The first dataset is `bestSelling_games.csv`. It contains 2,380 Steam games and includes information such as:

* Game name
* Price
* Estimated downloads
* Review information
* Game length
* Difficulty
* Tags
* Supported platforms

This dataset is used as the main source because it includes estimated downloads, which are used as the main popularity measure.

#### Enrichment Dataset

The second dataset is `steam_games_2026.csv`. It contains 1,000 Steam games and includes additional metadata such as:

* Game title
* Primary genre
* Review score
* Estimated owners
* 24-hour peak players
* Steam Deck status

This dataset is used to enrich the main dataset with additional variables such as primary genre and review score.

---

### 2.2 Data Processing Pipeline

Before analysis, both datasets were cleaned and merged.

The main steps were:

* Loaded both datasets using Python and pandas
* Cleaned game names by converting them to lowercase and removing extra spaces
* Merged the datasets based on game titles
* Checked the merged dataset size, column types, and missing values
* Created additional variables such as price categories and download categories

After merging the two datasets, 424 common games were retained for analysis.

---

## 3. Exploratory Data Analysis

Exploratory Data Analysis was conducted to understand the structure of the dataset and observe possible relationships before applying formal statistical tests.

---

### 3.1 Distribution of Estimated Downloads

Estimated downloads were highly right-skewed. Most games had relatively low estimated downloads, while a small number of games had extremely high download counts.

Because of this skewness, a logarithmic transformation was applied to estimated downloads. After applying the log transformation, the distribution became more balanced and easier to interpret.

This shows that Steam game popularity is unevenly distributed. A small number of highly successful games dominate the market, while most games attract smaller player bases.

---

### 3.2 Price and Downloads

A scatter plot was used in the EDA notebook to examine the relationship between price and log-transformed estimated downloads.

The analysis did not show a strong linear relationship between price and downloads. Although price may affect accessibility, the relationship between price and popularity is not simple. Some free games reach very high download counts, but some paid games also perform well.

This suggests that price alone is not enough to explain Steam game popularity.

---

### 3.3 Price Categories

To make the price analysis easier to interpret, games were grouped into price categories:

* Free
* Low
* Medium
* High

Average downloads were then compared across these categories.

Free games had the highest average downloads. High-priced games also showed relatively strong download numbers compared to low and medium-priced games.

This suggests that free games benefit from accessibility, but expensive games can also succeed if they have other strong factors such as brand recognition, quality perception, or marketing.

---

### 3.4 Genre Analysis

Average downloads were compared across game genres.

Action games had the highest average downloads among genres. Indie, Strategy, and RPG games also performed relatively well.

Some genres such as Racing had lower average downloads. This suggests that genre may influence popularity, but genre alone does not fully explain download behavior.

---

### 3.5 EDA Summary

The EDA shows that Steam game popularity is highly uneven. Free games tend to perform better in terms of downloads, and some genres such as Action appear more popular on average.

However, visual patterns alone are not enough to prove statistical significance. Therefore, hypothesis testing was applied in the next stage.

---

## 4. Hypothesis Testing

Several statistical tests were conducted to evaluate the relationships observed in the EDA.

---

### 4.1 Hypothesis 1: Free vs Paid Games

**Null Hypothesis:**  
There is no significant difference in average estimated downloads between free and paid games.

**Alternative Hypothesis:**  
There is a significant difference in average estimated downloads between free and paid games.

**Test Used:**  
Independent t-test

**Result:**  
The p-value was 7.73 × 10⁻⁸.

Since the p-value is significantly less than 0.05, the null hypothesis was rejected.

**Conclusion:**  
There is a statistically significant difference between free and paid games in terms of estimated downloads. Free games tend to have higher downloads on average. This supports the idea that accessibility plays an important role in game popularity.

---

### 4.2 Hypothesis 2: Genre and Download Category

**Null Hypothesis:**  
Game genre and download category are independent.

**Alternative Hypothesis:**  
Game genre and download category are not independent.

**Test Used:**  
Chi-square test

**Result:**  
The p-value was 0.1502.

Since the p-value is greater than 0.05, the null hypothesis was not rejected.

**Conclusion:**  
There is not enough statistical evidence to conclude that genre and download category are significantly related. Although the EDA showed visible differences between genres, especially for Action games, the chi-square test did not confirm a statistically significant relationship.

This may be due to high variability within genres and the loss of information caused by converting numerical downloads into categories.

---

### 4.3 Hypothesis 3: Review Score and Downloads

**Null Hypothesis:**  
There is no significant relationship between review score and estimated downloads.

**Alternative Hypothesis:**  
There is a significant relationship between review score and estimated downloads.

**Test Used:**  
Pearson correlation test

**Result:**  
The correlation coefficient was 0.0450 and the p-value was 0.3552.

Since the p-value is greater than 0.05, the null hypothesis was not rejected.

**Conclusion:**  
There is no statistically significant relationship between review score and log-transformed estimated downloads. The correlation value is also very close to zero, indicating an extremely weak relationship.

Therefore, review score alone does not appear to be an important factor in explaining game popularity.

---

### 4.4 Hypothesis 4: Price and Downloads

**Null Hypothesis:**  
There is no significant relationship between game price and estimated downloads.

**Alternative Hypothesis:**  
There is a significant relationship between game price and estimated downloads.

**Test Used:**  
Pearson correlation test

**Result:**  
The correlation coefficient was -0.0717 and the p-value was 0.1408.

Since the p-value is greater than 0.05, the null hypothesis was not rejected.

**Conclusion:**  
There is no statistically significant linear relationship between game price and log-transformed estimated downloads. The negative correlation suggests a slight tendency for higher-priced games to have lower downloads, but this relationship is very weak and not statistically significant.

This result also shows that although free games perform better than paid games in the t-test, price as a continuous variable does not strongly explain download differences on its own.

---

### 4.5 Overall Hypothesis Testing Result

The hypothesis testing results show mixed findings.

The independent t-test showed that free and paid games differ significantly in terms of estimated downloads. This suggests that price accessibility has an important relationship with game popularity when games are grouped as free or paid.

However, the chi-square test did not show a statistically significant relationship between genre and download category. The Pearson correlation tests also showed that review score and price do not have statistically significant linear relationships with log-transformed estimated downloads.

Overall, free games tend to perform better in terms of downloads, but Steam game popularity cannot be fully explained by price, genre, or review score alone.

---

## 5. Machine Learning Analysis

Machine learning methods were applied to examine whether game popularity can be predicted using simple game features.

---

### 5.1 Linear Regression

**Goal:**  
Predict log-transformed estimated downloads using price and review score.

**Features Used:**

* Price
* Review score

**Target Variable:**  
Log-transformed estimated downloads

**Evaluation Metric:**  
R² Score

**Result:**  
The Linear Regression model achieved a very low R² score of approximately 0.007.

**Interpretation:**  
This means that price and review score explain almost none of the variation in estimated downloads. The result suggests that these features alone are not sufficient to predict game popularity.

This finding is consistent with the Pearson correlation tests, where both price and review score showed very weak and statistically insignificant relationships with downloads.

---

### 5.2 Decision Tree Classifier

**Goal:**  
Classify games as popular or not popular.

Games were labeled as popular if their estimated downloads were above the median download count. Games below the median were labeled as not popular.

**Features Used:**

* Price
* Review score

**Evaluation Metric:**

* Accuracy
* Classification report

**Result:**  
The Decision Tree Classifier achieved an accuracy of approximately 0.447.

**Interpretation:**  
Since this is close to random guessing for a binary classification problem, the model did not perform strongly. This suggests that price and review score alone are not enough to classify games as popular or not popular.

The classification model supports the same conclusion as the regression model: simple variables such as price and review score are weak predictors of Steam game popularity.

---

### 5.3 Overall Machine Learning Result

The machine learning results show that game popularity is difficult to predict using only simple features such as price and review score.

This supports the earlier EDA and hypothesis testing findings. Steam game popularity is likely influenced by more complex factors such as marketing, brand recognition, community engagement, game visibility, social media attention, and player trends.

---

## 6. Key Findings

The main findings of this project are:

* Steam game downloads are highly skewed
* A small number of games dominate the market
* Free games tend to have significantly higher downloads than paid games
* Price does not show a strong linear relationship with downloads
* Genre differences are visible in EDA, especially for Action games
* Genre was not statistically significant in the chi-square test
* Review score was not significantly correlated with downloads
* Price and review score alone are weak predictors of popularity in machine learning models
* Steam game popularity is likely influenced by more complex external factors

---

## 7. Limitations and Future Work

This project has several limitations that should be considered when interpreting the results.

First, after merging the two datasets, the final dataset contained 424 common games. Although this is sufficient for exploratory analysis, hypothesis testing, and basic machine learning models, it is smaller than the original datasets. Some games may not have matched because of differences in naming between the two sources.

Second, estimated downloads were used as a proxy for game popularity. While this is useful for analysis, it may not perfectly represent active player engagement, long-term retention, or addictiveness. A game may have many downloads but low active player retention, or fewer downloads but a highly engaged player base.

Third, the machine learning models used only price and review score as input features. These variables were useful for testing basic predictive relationships, but the results suggest that they are not sufficient on their own to explain Steam game popularity.

For future work, the analysis could be improved by adding stronger features such as:

* Marketing visibility
* Wishlist counts
* Social media activity
* Player retention
* Multiplayer activity
* Update frequency
* Community size
* More detailed Steam player statistics

Future models could also include more game design-related variables and larger datasets. However, the current results already show an important finding: Steam game popularity is complex and cannot be explained only by simple variables such as price and review score.

---

## 8. AI Usage Disclaimer

In this project, AI tools such as ChatGPT were used for:

* Understanding statistical concepts such as hypothesis testing, t-test, chi-square, Pearson correlation, and machine learning evaluation
* Debugging code and fixing errors
* Structuring the project and improving explanations

All analysis steps, decisions, and interpretations were reviewed and finalized by the author.

---

## 9. References and Tools

**Programming Language:**  
Python

**Libraries Used:**

* pandas
* numpy
* matplotlib
* scipy
* scikit-learn

**Datasets:**

* `bestSelling_games.csv`
* `steam_games_2026.csv`
