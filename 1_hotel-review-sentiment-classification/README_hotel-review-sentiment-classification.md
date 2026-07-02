# Hotel Review Sentiment Classification

Predicts sentiment from hotel review text and explores which approach works best: a trained classifier, a rule-based lexicon, or a combination of both.

## Dataset

A sample of 30,000 hotel reviews, each with review text and an overall star rating. Ratings are used as the sentiment label for classification.

## Approach

**1. Exploratory analysis**
Reviewed the distribution of ratings and ran word frequency analysis to understand common vocabulary in the reviews.

**2. Preprocessing**
Lowercased text, removed punctuation, tokenised with spaCy, removed stopwords, and applied lemmatisation before converting text into TF-IDF and CountVectorizer features. Class imbalance across rating categories was handled with upsampling and downsampling.

**3. Supervised classification**
Trained a Multinomial Naive Bayes classifier, chosen because it works well with the sparse, high-dimensional features that TF-IDF and CountVectorizer produce, and is efficient on large text datasets compared to alternatives like SVM or Random Forest. Evaluated with 10-fold cross-validation.

**4. Lexicon-based baseline**
Compared the trained classifier against VADER, a rule-based sentiment lexicon that does not learn from the data.

**5. Hybrid model**
Combined VADER and Multinomial Naive Bayes to test whether merging a rule-based and a learned approach improves results, based on prior published work on hybrid sentiment models.

**6. Aspect-level prediction**
Extended the task to multi-output classification, predicting sentiment across multiple review aspects at once rather than a single overall rating.

## Result

The trained Multinomial Naive Bayes classifier consistently outperformed the VADER lexicon baseline. VADER's rule-based scoring does not adapt to the specific vocabulary and patterns in the dataset, while the TF-IDF and Naive Bayes combination captures those patterns directly from the data, resulting in more accurate and better-balanced predictions.

## Tech stack

Python, pandas, scikit-learn, NLTK, spaCy, VADER, matplotlib/seaborn

## File

`hotel-review-sentiment-classification.ipynb`