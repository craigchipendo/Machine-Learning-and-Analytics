# Twitter Sentiment Analysis: Classical ML vs. LSTM

## Overview
An NLP pipeline that classifies the sentiment (positive or negative) of X (Twitter) posts. The same approach can be used to track customer sentiment toward brands and products. The project compares classical machine learning models on TF-IDF features with a deep learning model (LSTM on Word2Vec embeddings), trained on about 1.5 million labelled tweets.

## Data
- **Training set:** 1,523,975 tweets (767,059 negative, 756,916 positive)
- **Test set:** 359 tweets (177 negative, 182 positive), after removing neutral labels
- **Preprocessing:** removed blanks, duplicates and neutral test labels; cleaned text (mentions, URLs, non-alphanumeric characters); lemmatization; explored sentence lengths and unknown tokens with a `distilroberta-base` tokenizer

## Models
### Classical models (scikit-learn)
TF-IDF vectorizer (word 1-2 grams), then:

| Model | Test accuracy | Macro F1 |
|---|---:|---:|
| Bernoulli Naive Bayes | 0.83 | 0.83 |
| Linear SVC | 0.82 | 0.82 |
| Logistic Regression | 0.82 | 0.82 |

### Deep learning model (Keras / TensorFlow)
- **Word2Vec embeddings** (gensim): 300 dimensions, window 7, vocabulary of 33,070 words, used as a frozen embedding layer
- **Architecture:** Embedding, Dropout (0.5), **LSTM** (100 units, dropout 0.2), Dense (sigmoid)
- **Training:** 1 epoch, batch size 1,024, 10% validation split, reduce-learning-rate and early-stopping callbacks (about 8 hours on CPU)
- **Results:** validation accuracy 0.764; **test accuracy 0.811**
- Prediction function maps the score to NEGATIVE / NEUTRAL / POSITIVE using thresholds (0.4, 0.7)

## Key finding
On this test set, the simpler TF-IDF + Naive Bayes model (0.83) slightly outperformed the LSTM (0.81). The LSTM was trained for only one epoch, so more training and a larger test set would be the next steps before choosing a model.

## Files
- `Exploring Data.ipynb`: data cleaning and exploration
- `Twitter.ipynb`: classical models, Word2Vec + LSTM model, evaluation and prediction
- `Sentiment-LR.pickle`, `Sentiment-BNB.pickle`: saved classical models
- `Sentiment-LSTM.pickle`: saved LSTM training history

## Tools
Python, pandas, NumPy, scikit-learn, TensorFlow / Keras, gensim (Word2Vec), NLTK, Hugging Face Transformers (tokenizer), Matplotlib, Seaborn
