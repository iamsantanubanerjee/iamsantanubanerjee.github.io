---
title: "Basic Terminologies"
description: ""
summary: ""
date: 2024-02-29T19:21:13+05:30
lastmod: 2024-02-29T19:21:13+05:30
draft: false
menu:
  statistics:
    parent: ""
    identifier: "basic-terminologies"
weight: 2
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Tokenization

**Tokenization** is the process of breaking sentences into words.

For example, let us take the most iconic dialogue of all time from Bram Stroker's "Dracula":

```
I have crossed oceans of time to find you.
```

The above when tokenized using the [Natural Language Toolkit (NLTK)](https://www.nltk.org/) library gives us a list as follows:

```
['I', 'have', 'crossed', 'oceans', 'of', 'time', 'to', 'find', 'you', '.']
```

## Stopwords

**Stopwords** are words which do not add much value to the overall meaning of a sentence. Such words include: "this", "of", "and", etc. They are usually deleted as a pre-processing technique from a dataset so as to reduce complexity, allowing our nlp model to focus more on important words.

From our previous [example](#tokenization), the tokens we would be left with after removing the stopwords will be:
```
['crossed', 'oceans', 'time', 'find', '.']
```

## Stemming

**Advantages**

**Disadvantages**

## Lemmatization

**Advantages**

**Disadvantages**

## Word embeddings

It is a technique where individual words are represented as real-valued vectors in a lower-dimensional space and captures inter-word semantics.

### Types of word embeddings

Based on the technique used, word embeddings can be divided into two parts:
1. **Count or frequency** - This includes techniques such as One-Hot Encoding, Bag of Words and TF-IDF
2. **Deep Learning Trained Models** - Word2Vec (CBOW, Skipgram)