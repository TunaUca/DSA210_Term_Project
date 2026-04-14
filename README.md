# DSA210 Term Project

## Project Overview
This project analyzes factors that influence the popularity of Steam games, using estimated downloads as a measure of popularity.

The main focus is to explore how variables such as **price** and **genre** affect game popularity.

---

## Dataset
Two datasets are used in this project:

- `bestSelling_games.csv`: Contains estimated downloads and basic game information
- `steam_games_2026.csv`: Contains metadata such as price, genre, and review scores

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
- Chi-square test to examine relationship between genre and download categories

---

## Current Findings
- Download distribution is highly skewed, with a few games dominating the market
- Free games tend to have higher downloads
- Price does not show a strong linear relationship with downloads
- Genre differences are visible in EDA but not statistically significant in chi-square test

---

## Project Structure

---

## Status
This project currently includes:
- Exploratory Data Analysis
- Hypothesis Testing
