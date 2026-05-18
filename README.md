# Steam Game Popularity Analysis

DSA210 Term Project

---

## Overview

This project analyzes factors that influence the popularity of Steam games.

The main objective is to examine whether variables such as price, genre, review score, and other game-related features have an effect on estimated downloads.

The project is structured in three main parts:

* Exploratory Data Analysis (EDA)
* Hypothesis Testing
* Machine Learning

---

## Motivation

Game popularity is influenced by many factors and is not always easy to predict.

In particular, popularity may change based on:

* Price
* Genre
* Review score
* Player engagement and visibility

Understanding these patterns can provide insights into what types of games attract larger player bases on Steam.

---

## Data

### Main Steam Dataset

* Source: Kaggle
* File: `bestSelling_games.csv`
* Contains 2,380 Steam games
* Includes features such as:
  * Game name
  * Price
  * Estimated downloads
  * Review information
  * Game length
  * Difficulty
  * Tags and supported platforms

### Enrichment Dataset

* Source: Kaggle
* File: `steam_games_2026.csv`
* Contains 1,000 Steam games
* Includes features such as:
  * Game title
  * Primary genre
  * Review score
  * Estimated owners
  * 24-hour peak players
  * Steam Deck status

The datasets were cleaned and merged based on game names. After merging, 424 common games were retained for analysis.

---

## Methodology

### Data Preparation

* Loaded both datasets using Python
* Cleaned game names by converting them to lowercase and removing extra spaces
* Merged the datasets based on game titles
* Checked dataset size, column types, and missing values
* Created additional variables such as price categories and download categories when needed

---

## Exploratory Data Analysis (EDA)

EDA was conducted to explore patterns before applying statistical methods.

### Analyses Conducted

* General dataset overview
* Distribution of estimated downloads
* Log transformation of downloads due to skewness
* Distribution of game prices
* Relationship between price and downloads
* Average downloads by price category
* Average downloads by genre
* Relationship between review score and downloads

### Observations

* Estimated downloads are highly skewed, with a small number of games dominating the market
* Log transformation makes the download distribution easier to interpret
* Many games are concentrated in lower price ranges
* Price does not show a strong linear relationship with downloads
* Free games tend to have higher average downloads
* Action games have the highest average downloads among genres
* Review score has only a weak relationship with downloads

---

## Hypothesis Testing

Statistical tests were conducted to evaluate relationships observed in the EDA.

### Hypotheses Tested

#### 1. Free vs Paid Games

* Null Hypothesis: There is no significant difference in average estimated downloads between free and paid games.
* Alternative Hypothesis: There is a significant difference in average estimated downloads between free and paid games.
* Test Used: Independent t-test
* Result: Reject H0
* Interpretation: Free and paid games differ significantly in terms of estimated downloads. Free games tend to have higher downloads.

#### 2. Genre and Download Category

* Null Hypothesis: Game genre and download category are independent.
* Alternative Hypothesis: Game genre and download category are not independent.
* Test Used: Chi-square test
* Result: Fail to reject H0
* Interpretation: The chi-square test did not show a statistically significant relationship between genre and download category. Although genre differences were visible in EDA, they were not strongly supported by this test.

#### 3. Review Score and Downloads

* Null Hypothesis: There is no significant relationship between review score and estimated downloads.
* Alternative Hypothesis: There is a significant relationship between review score and estimated downloads.
* Test Used: Pearson correlation test
* Result: Fail to reject H0
* Interpretation: Review score did not show a statistically significant relationship with log-transformed estimated downloads. The correlation was very weak, meaning review score alone does not strongly explain game popularity.

#### 4. Price and Downloads

* Null Hypothesis: There is no significant relationship between game price and estimated downloads.
* Alternative Hypothesis: There is a significant relationship between game price and estimated downloads.
* Test Used: Pearson correlation test
* Result: Fail to reject H0
* Interpretation: Price did not show a statistically significant linear relationship with log-transformed estimated downloads. Although free games performed better than paid games in the t-test, price as a continuous variable was not a strong standalone predictor.

### Overall Hypothesis Testing Result

The hypothesis testing results show that price accessibility matters when comparing free and paid games. However, genre, review score, and price alone do not fully explain Steam game popularity.

This suggests that game popularity is influenced by more complex factors such as marketing, brand recognition, community activity, visibility, and player trends.

---

## Machine Learning

The final stage of the project applies machine learning methods to examine whether game popularity can be predicted from simple game features.

### Approach

Since game popularity can be represented numerically using estimated downloads, one part of the ML analysis is treated as a regression task.

A second model treats popularity as a classification task by labeling games as popular or not popular based on the median download count.

### Models Used

* Linear Regression → predicts log-transformed estimated downloads
* Decision Tree Classifier → classifies games as popular or not popular

### Features

* Price
* Review score

### Evaluation Metrics

* R² Score for Linear Regression
* Accuracy and classification report for Decision Tree Classifier

### Results

* The Linear Regression model achieved a very low R² score
* This indicates that price and review score explain very little of the variation in downloads
* The Decision Tree Classifier also showed weak classification performance
* This suggests that simple features alone are not sufficient to predict game popularity accurately

### Interpretation

The machine learning results support the earlier EDA and hypothesis testing findings.

Price and review score alone are not strong predictors of game popularity. Steam game popularity is likely influenced by more complex factors such as genre, marketing, brand recognition, community activity, and player trends.

---

## Key Findings

* Steam game downloads are highly skewed
* A small number of games dominate the market
* Free games tend to have significantly higher downloads than paid games
* Price does not show a strong linear relationship with downloads
* Genre differences are visible in EDA, especially for Action games
* Genre was not statistically significant in the chi-square test
* Review score was not significantly correlated with downloads
* Machine learning models show that price and review score alone are weak predictors of popularity

---

## Project Structure

* `EDA.ipynb` → Exploratory Data Analysis
* `hypothesis_testing.ipynb` → Hypothesis Testing
* `machine_learning.ipynb` → Machine Learning
* `bestSelling_games.csv` → Main Steam dataset
* `steam_games_2026.csv` → Enrichment dataset
* `requirements.txt` → Python dependencies
* `README.md` → Project overview

---

## Requirements

The required Python libraries are listed in `requirements.txt`.

Main dependencies:

* pandas
* numpy
* matplotlib
* scipy
* scikit-learn

---

## AI Usage

AI tools such as ChatGPT were used for:

* Understanding statistical concepts such as hypothesis testing, t-test, chi-square, Pearson correlation, and machine learning evaluation
* Debugging code and fixing errors
* Structuring the project and improving explanations

All analysis steps, decisions, and interpretations were made by the author.
