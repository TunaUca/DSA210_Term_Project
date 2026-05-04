# DSA210 Term Project

## Project Overview
This project analyzes factors that influence the popularity of Steam games, using estimated downloads as a measure of popularity.

The main focus is to explore how variables such as **price**, **genre**, and **review score** affect game popularity.

---

## Dataset
Two datasets are used in this project:

- `bestSelling_games.csv`: Contains estimated downloads and basic game information
- `steam_games_2026.csv`: Contains metadata such as price, genre, review scores, and other game-related features

The datasets are cleaned and merged based on game names.

---

## Exploratory Data Analysis (EDA)
The EDA is conducted in `EDA.ipynb`.

Main steps:
- Analysis of download distribution
- Log transformation of downloads due to skewness
- Price distribution and price categories
- Relationship between price and downloads
- Analysis of average downloads by genre

---

## Hypothesis Testing
The hypothesis testing is conducted in `hypothesis_testing.ipynb`.

Tests performed:
- Independent t-test to compare free vs paid games
- Chi-square test to examine the relationship between genre and download categories

---

## Machine Learning
The machine learning analysis is conducted in `machine_learning.ipynb`.

Models applied:
- Linear Regression to predict log-transformed estimated downloads
- Decision Tree Classifier to classify games as popular or not popular

The machine learning results suggest that price and review score alone are not strong predictors of game popularity.

---

## Current Findings
- Download distribution is highly skewed, with a few games dominating the market
- Free games tend to have higher downloads
- Price does not show a strong linear relationship with downloads
- Genre differences are visible in EDA but are not statistically significant in the chi-square test
- Machine learning models show that simple features such as price and review score are not sufficient to strongly predict popularity

---

## Project Structure
```text
EDA.ipynb
hypothesis_testing.ipynb
machine_learning.ipynb
bestSelling_games.csv
steam_games_2026.csv
requirements.txt
README.md
```

---

## Requirements
The required Python libraries are listed in `requirements.txt`.

Main dependencies:
- pandas
- numpy
- matplotlib
- scipy
- scikit-learn

---

## Status
This project currently includes:
- Exploratory Data Analysis
- Hypothesis Testing
- Machine Learning

---

## AI Usage Disclaimer
In this project, AI tools such as ChatGPT were used for:

- Understanding statistical concepts such as hypothesis testing, t-test, chi-square, and machine learning evaluation
- Debugging code and fixing errors
- Structuring the project and improving explanations

All analysis, interpretations, and final decisions were made by the author.
