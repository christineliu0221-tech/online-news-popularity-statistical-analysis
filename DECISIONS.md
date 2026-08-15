# Decision Log

These entries were compiled from the submitted Assignment 2–6 workbooks and their Commentary sheets. They summarize decisions already reflected in the team's work rather than introducing new analysis.

## Assignment 2: Dataset selection — 2026-07-19

- **Dataset:** Online News Popularity from the UCI Machine Learning Repository.
- **Primary outcome:** `shares`, the number of times an article was shared on social networks.
- **Why we chose it:** The dataset offered many variables and a relevant question—what characteristics are associated with online content becoming popular. Its subject matter also connects to the team's everyday experience with online media.
- **Key preparation decisions:** We trimmed whitespace from column names; reconstructed the original one-hot data-channel fields into three broader subject categories; combined weekday indicators into a Weekday/Weekend variable; and binned title sentiment polarity into Negative, Neutral, and Positive categories.
- **Analysis fields:** We retained 17 continuous variables, three categorical variables, `shares`, and a binary popularity field based on the median threshold of 1,400 shares. No data values were fabricated or simulated.

## Assignment 3: Descriptive statistics and visualization — 2026-07-26

- **Focused analysis file:** We reduced the working dataset to six interpretable continuous predictors, three categorical predictors, and the `shares` outcome, producing 39,644 observations across 10 columns.
- **Data-quality decision:** The selected variables had no missing values and no duplicate rows across the 10-column analysis file. We did not impute, standardize, winsorize, or otherwise change numeric values.
- **Important pattern:** Several variables were heavily right-skewed. This was most pronounced for `shares`, where the mean was about 3,395 and the median was 1,400. We therefore treated the median as a better description of a typical article and interpreted mean-based summaries cautiously.
- **Next-step decision:** Simple correlations between the six continuous predictors and `shares` were weak. We flagged possible interactions, nonlinear relationships, and a potential log transformation of `shares` as useful future directions.

## Assignment 4: Probability and distributions — 2026-07-26

- **Distribution assessment:** Of the seven continuous variables assessed, headline word count (`n_tokens_title`) and global sentiment polarity were the closest to normal. Article length, hyperlinks, images, keyword popularity, and shares were strongly right-skewed.
- **Variable selected for probability scenarios:** We chose `n_tokens_title` because headline length is under an editor's control and its approximately normal distribution supported z-score calculations.
- **Method decision:** We used a normal model for the headline-length scenarios rather than applying normal assumptions to the strongly skewed variables.
- **Results used in interpretation:** The fitted model estimated about a 2.6% probability of a title longer than 14 words, a 3.3% probability of a title shorter than 7 words, and an 84.4% probability of a title between 8 and 13 words.

## Assignment 5: Hypothesis testing and confidence intervals — 2026-08-09

- **Significance level:** We set `α = 0.05` for both one-sample, right-tailed t-tests.
- **Headline-length test:** We tested whether the population mean headline length exceeded 10 words. The sample mean was approximately 10.399 words, and we rejected the null hypothesis (`t = 37.56`, `df = 39,643`, reported `p < 0.000001`).
- **Sentiment test:** We tested whether mean global sentiment polarity was greater than zero. The sample mean was approximately 0.119, and we rejected the null hypothesis (`t = 245.08`, `df = 39,643`, reported `p < 0.000001`).
- **Confidence interval:** The 95% confidence interval for the population mean number of shares was approximately 3,280.93 to 3,509.83.
- **Assumption judgment:** The very large sample supported approximate normality of the sampling distributions. We treated article-level independence as reasonable but not fully verifiable, and we retained cautions about extreme outliers and representativeness.

## Assignment 6: Regression modeling — 2026-08-12

- **Model-building approach:** We began with all candidate predictors and used backward removal, dropping the predictor with the largest p-value above 0.05 before rerunning the model.
- **First predictor removed:** The Neutral title-sentiment indicator was removed first because it had the highest nonsignificant p-value in the initial model.
- **Subsequent removals:** Global sentiment polarity, article word count, headline word count, the Positive title-sentiment indicator, and the Weekday indicator were removed in later iterations because each was the largest remaining nonsignificant p-value at that stage.
- **Final model:** The retained predictors were number of hyperlinks, number of images, historical average keyword popularity, the Tech/Business subject indicator, and the World/Other subject indicator. All five were statistically significant at the 5% level.
- **Multicollinearity decision:** The team compared correlations among the three retained continuous predictors against a 0.70 concern threshold and concluded that none required removal for multicollinearity.
- **Interpretation:** The final model had `R² = 0.0137`, explaining only about 1.4% of the variation in shares. The large sample made it possible to identify statistically significant associations even though explanatory power was weak. We therefore treated the model as an exploratory guide to possible factors associated with sharing, not as a reliable prediction tool or evidence of causation.
