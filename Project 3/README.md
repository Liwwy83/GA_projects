# Project 3 - Japanese or Korean?

## Problem Statement
This project aims to help potential learners who wish to pick up a foreign languages decide on which language is more favourable. The scope is narrowed down to Japanese and Korean, languages that are similar on many fronts. See this [wikipedia page](https://en.wikipedia.org/wiki/Comparison_of_Japanese_and_Korean) for a comparison.

## Web Scraping and Data Cleaning
1000 posts comprising the 'title' and the 'selftext' were retrieved from the subreddits:
- [LearnJapanese](https://www.reddit.com/r/LearnJapanese/new)
- [korean](https://www.reddit.com/r/korean/new)

After data cleaning, there were 995 and 976 Japanese and Korean posts.

## Data Analysis
### Posting Patterns
|Subreddit|Number of Words|Number of Non-English Characters|
|---|---|---|
|Japanese|More Words|Fewer non-English characters|
|Korean|Fewer Words|More non-English characters|

### Sentiment Analysis
=================== Japanese ==================
Positive: Average is 0.116, Proportion is 0.687
Negative: Average is 0.037, Proportion is 0.155

==================== Korean ===================
Positive: Average is 0.12, Proportion is 0.642
Negative: Average is 0.031, Proportion is 0.121

### Recommendations to Potential Learners
Japanese is more suitable for learners who
1) already can speak a language that has pitch accent or tones, such as Mandarin, Punjabi or Swedish;

2) have experience with or are interested in picking up logographic characters (Kanji) and not limit themselves to a phonologic writing system with a fixed set of alphabet.

Usage of the Korean subreddit is recommended for beginners, as the posts have fewer negative sentiments (thus may be more encouraging) and the words frequently used indicate a helpful environment, whereas usage of the Japanese subreddit may be more suitable for intermediate learners.

## Classification by Machine Learning
6 models, using algorithms Multinomial Naive-Bayes, Logistic Regression or Random Forest Classifier, with CountVectorizer or TfidfVectorizer, were trained and tuned.

### Summary of Results
|Algorithm|Vectorizer|Best Score|Train Score|Test Score|f1 Score|Sensitivity|Specificity|
|---|---|---|---|---|---|---|---|
|Multinomial Naive-Bayes|CountVectorizer|0.763|0.894|0.793|0.79|0.82|0.77|
|Multinomial Naive-Bayes|TfidfVectorizer|0.761|0.946|0.785|0.78|0.82|0.75|
|Logistic Regression|CountVectorizer|0.760|0.970|0.763|0.76|0.70|0.83|
|Logistic Regression|TfidfVectorizer|0.746|0.922|0.769|0.77|0.71|0.82|
|Random Forest Classifier|CountVectorizer|0.760|0.985|0.753|0.75|0.73|0.77|
|Random Forest Classifier|CountVectorizer|0.765|0.993|0.726|0.73|0.67|0.79|

All models run are at least 20% more accurate than the baseline accuracy of 0.505, where all posts are predicted to be from the Japanese subreddit.

### Testing on New Data
To check for future compatibility, one model for each of the 3 algorithms is selected and trained using the original full set of data (from 1 Jan 2021 onwards) for use on future posts, to ensure that the models are not adversely affected by recent trends. They are tested on 100 newest posts (retrieved on 20 Jan 2022) from each subreddit, and their performances are evaluated.

### Conclusion
There are sufficient differences between the 2 subreddits as 2 of the 3 trained models (Multinomial Naive-Bayes and Random Forest Classifier) accurately predict which subreddit the posts come from for more than 75% of the time. The Random Forest Classifier is chosen to be the production model as it did not assign very high probabilities to the misclassified posts.

## Possible Improvements in Future
1. This project used only 1000 posts from each subreddit. To improve the model, more posts can be scraped from the web so that more data could be used for training.
2. More hyperparameter tuning could be attempted to improve the models if there was more time.
3. The results of the 3 models could be combined using Voting Classifier.