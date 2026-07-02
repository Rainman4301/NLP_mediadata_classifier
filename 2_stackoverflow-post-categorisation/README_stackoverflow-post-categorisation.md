# Stack Overflow Post Categorisation

A system that collects NLP-related questions and answers from Stack Overflow and automatically groups them into 12 task-based categories, so developers can navigate common problems and solutions more easily. Built as a two-person mini-project.

## Data collection

Used the Stack Exchange API to collect around 20,000 posts through four rounds of requests, progressively widening the search from the NLP collective, to NLP-related tags, to broader tags, in order to reach the target dataset size while keeping the content focused on NLP topics. Duplicate posts were removed by checking question IDs across requests.

## Exploratory analysis

- Reviewed score, view count, and answer count distributions, and their correlation with title, body, and answer length
- Analysed which tags receive the highest engagement
- Tracked posting volume and view count trends from 2008 to 2025
- Built word clouds and frequency charts across the title, body, and combined title+body text, which showed that the title field carries the most topic-relevant signal for classification

## Preprocessing

Tested combinations of regex cleaning (removing HTML tags and code blocks), lowercasing, lemmatisation, and stopword removal to identify which combination produced the cleanest, most useful text for categorisation.

## Categorisation approach

**Category definition:** Used BERTopic for initial topic discovery, then defined 12 NLP task categories with a curated list of top keywords per category based on the discovered topics and domain knowledge.

**Two classification methods were compared:**
1. **Rule-based model** – scores text against the category keyword lists and assigns the highest-scoring category, or "other" if no keywords match.
2. **Cosine similarity with sentence embeddings** – embeds posts and category keyword sets using SBERT and CodeBERT, then assigns each post to its closest category by cosine similarity. SBERT produced more distinct, useful embeddings than CodeBERT, which tended to score most posts as very similar to everything.

**Evaluation:** Since the task is unsupervised, used silhouette score alongside intra-cluster and inter-cluster distance to judge which method separated categories more clearly.

**Experiments:** Compared the rule-based and cosine similarity methods across the three text fields (title, body, title+body) and across preprocessing combinations, then further tested whether adding POS tagging and dependency parsing improved category separation.

## Final pipeline

Cosine similarity with SBERT embeddings, using the post title with lemmatisation, POS tagging, and dependency parsing, and a similarity threshold of 0.3 to separate confident matches from the "other" category. This combination gave the best evaluation scores across all methods tested.

## Tech stack

Python, pandas, Stack Exchange API, spaCy, BERTopic, Sentence-Transformers (SBERT), CodeBERT, scikit-learn

## Files

`stackoverflow_post_categorisation.ipynb` — full pipeline from data collection to final classification