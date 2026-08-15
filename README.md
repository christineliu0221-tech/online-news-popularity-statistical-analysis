# Online News Popularity: Statistical Analysis

An Excel-based statistics project examining which article characteristics are associated with the number of times an online news article is shared.

## Project overview

This project follows one dataset through data selection, descriptive statistics, probability, statistical inference, and multiple regression. The central research question is:

> Which measurable characteristics of an online news article are associated with its number of social-media shares, and how well can those characteristics explain article popularity?

## Dataset

The project uses the **Online News Popularity** dataset from the UCI Machine Learning Repository. It contains information about 39,644 articles published by Mashable, including headline and article length, links and images, keyword history, sentiment, publication timing, subject category, and the number of shares.

The original source contains 60 predictor attributes plus the article URL and shares outcome. Assignment 2 produced a curated workbook with 23 analysis fields. Assignments 3–6 then used a focused 10-column analysis file containing six continuous predictors, three categorical predictors, and the outcome variable `shares`.

## Analysis progression

| Assignment | Focus | Main work |
|---|---|---|
| 2 | Dataset selection | Selected the UCI dataset, documented its source, reconstructed categorical variables, and identified `shares` as the primary outcome. |
| 3 | Descriptive statistics and visualization | Checked data quality, summarized continuous and categorical variables, and examined distributions and bivariate patterns. |
| 4 | Probability and distributions | Assessed normality and used headline length for normal-distribution probability scenarios. |
| 5 | Inference | Conducted two one-sample t-tests and constructed a 95% confidence interval for mean shares. |
| 6 | Regression | Used backward variable removal to develop a final multiple-regression model and assessed multicollinearity. |

## Selected findings

- The `shares` outcome is extremely right-skewed: the mean is about 3,395 shares, while the median is 1,400. A small number of viral articles strongly influence the mean.
- Headline length is approximately normally distributed. About 84.4% of articles have titles between 8 and 13 words under the fitted normal model.
- At the 5% significance level, the analysis found evidence that mean headline length exceeds 10 words and that mean global sentiment polarity is positive.
- The 95% confidence interval for mean shares is approximately 3,281 to 3,510 shares. This interval estimates the population mean, not the performance of a typical individual article.
- The final regression retained number of hyperlinks, number of images, historical keyword popularity, and two subject-category indicators. Although all five retained predictors were statistically significant, the model explained only about 1.4% of the variation in shares (`R² = 0.0137`). The results are therefore better treated as exploratory associations than as a strong prediction system.

## Repository structure

```text
online-news-popularity-statistical-analysis/
├── README.md
├── DECISIONS.md
├── data/
│   └── README.md
├── assignment-02-dataset/
├── assignment-03-descriptive-statistics/
├── assignment-04-probability-distributions/
├── assignment-05-inference/
└── assignment-06-regression/
```

Each assignment folder contains the Excel workbook submitted for that stage of the course project. The `data` folder documents the source dataset without duplicating the large raw dataset already embedded in the Assignment 2 workbook.

## Author and collaboration

**Christine Liu**

The statistical analysis was completed collaboratively as a team. This repository is Christine Liu's individual course submission and project record.

## Tools

- Microsoft Excel
- Descriptive statistics and data visualization
- Probability models
- One-sample t-tests and confidence intervals
- Multiple linear regression
- Git and GitHub for project organization and version history

## Data source

Fernandes, K., Vinagre, P., Cortez, P., and Sernadela, P. (2015). *Online News Popularity*. UCI Machine Learning Repository. https://doi.org/10.24432/C5NS3V

Dataset page: https://archive.ics.uci.edu/dataset/332/online+news+popularity

## AI-assistance disclosure

AI assistants were used during the coursework to help polish English expression, troubleshoot and verify Excel formulas, check formatting consistency, and organize project documentation. The dataset selection, statistical work, analytical decisions, and conclusions reflect the team's work and judgment.
