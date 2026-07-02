# NLP Portfolio

Two natural language processing projects completed during my Master of Data Science at the University of Adelaide. Both projects go through the full pipeline: data collection or cleaning, exploratory analysis, preprocessing, modelling, and evaluation.

## Projects

### 1. [Hotel Review Sentiment Classification](./1_hotel-review-sentiment-classification)
Predicts customer sentiment from hotel review text using classic NLP feature extraction (TF-IDF, CountVectorizer) and a Multinomial Naive Bayes classifier, benchmarked against the VADER lexicon and a hybrid model that combines both. Also extends into aspect-level sentiment prediction with a multi-output classifier.

**Key skills:** text preprocessing, TF-IDF/CountVectorizer, Multinomial Naive Bayes, lexicon-based sentiment analysis (VADER), 10-fold cross-validation, multi-output classification

### 2. [Stack Overflow Post Categorisation](./2_stackoverflow-post-categorisation)
Builds an end-to-end system that collects Stack Overflow questions through the Stack Exchange API and automatically groups them into 12 NLP task categories. Compares a rule-based keyword model against sentence embedding similarity (SBERT, CodeBERT), with topic discovery via BERTopic and evaluation using silhouette score and cluster distance metrics.

**Key skills:** API-based data collection, BERTopic, sentence embeddings (SBERT/CodeBERT), cosine similarity, unsupervised evaluation, POS tagging and dependency parsing

## Tech stack

Python, pandas, scikit-learn, NLTK, spaCy, Sentence-Transformers, BERTopic, matplotlib/seaborn

## Structure

```
NLP-Portfolio/
├── .env.example
├── .gitignore
├── README.md
├── 1_hotel-review-sentiment-classification/
│   ├── README_hotel-review-sentiment-classification.md
│   └── hotel-review-sentiment-classification.ipynb
└── 2_stackoverflow-post-categorisation/
    ├── README_stackoverflow-post-categorisation.md
    └── stackoverflow_post_categorisation.ipynb
```

Each project folder has its own README with dataset details, methodology, and results.

## Note on AI tool use

Some notebook cells include short comments marking where an AI assistant (GPT-4o) was used to help organise imports or explain a library function. This reflects how the code was actually written and is kept for transparency.