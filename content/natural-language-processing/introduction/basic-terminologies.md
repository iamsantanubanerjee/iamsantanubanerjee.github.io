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

> I have crossed oceans of time to find you.

The above when tokenized using the [Natural Language Toolkit (NLTK)](https://www.nltk.org/) library gives us a list as follows:

> ['I', 'have', 'crossed', 'oceans', 'of', 'time', 'to', 'find', 'you', '.']

**Example Code**
```python
import nltk
from nltk.tokenize import word_tokenize

nltk.download("punkt")  # Download the necessary data for word_tokenize

sentence = "I have crossed oceans of time to find you."
tokens = word_tokenize(sentence)

print("Original Sentence:", sentence)
print("Tokenized Sentence:", tokens)
```

**Output**
```
 Original Sentence: I have crossed oceans of time to find you.
 Tokenized Sentence: ['I', 'have', 'crossed', 'oceans', 'of', 'time', 'to', 'find', 'you', '.']
```

## Stopwords

**Stopwords** are words which do not add much value to the overall meaning of a sentence. Such words include: "this", "of", "and", etc. They are usually deleted as a pre-processing technique from a dataset so as to reduce complexity, allowing our nlp model to focus more on important words.

From our previous [example](#tokenization), the tokens we would be left with after removing the stopwords will be:

> ['crossed', 'oceans', 'time', 'find', '.']

**Example Code**
```python
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords

nltk.download("punkt")  # Download the necessary data for word_tokenize
nltk.download("stopwords")  # Download the stopwords dataset

sentence = "I have crossed oceans of time to find you."
tokens = word_tokenize(sentence)

stop_words = set(stopwords.words("english"))
filtered_tokens = [word for word in tokens if word.lower() not in stop_words]

print("Original Sentence:", sentence)
print("Tokens after removing stopwords:", filtered_tokens)
```

**Output**
```
 Original Sentence: I have crossed oceans of time to find you.
 Tokens after removing stopwords: ['crossed', 'oceans', 'time', 'find', '.']
```

## Stemming

**Stemming** is a process that stems or removes last few characters from a word, often leading to incorrect meanings and spelling.

For example, the words "Historical" and "History" will give the output as "histor" and "histori" respectively, thus, losing their meaning.

**Advantages**

* Stemming is really fast

**Disadvantages**

* Stemming removes the meaning of the word

**Example Code**

```python
import nltk
from nltk.stem import PorterStemmer

# Create a PorterStemmer instance
porter_stemmer = PorterStemmer()

stemmed_word1 = porter_stemmer.stem("Historical")
stemmed_word2 = porter_stemmer.stem("History")

print(stemmed_word1)
print(stemmed_word2)
```

**Output**
```
 histor
 histori
```

## Lemmatization

**Lemmatization** considers the context and converts the word to its meaningful base form, which is called Lemma.

**Advantages**

* Retains meaning of words

**Disadvantages**

* Computationally more expensive than Stemming (has it's own library to come up with the base/root word)

**Example Code**
```python
import nltk
from nltk.stem import WordNetLemmatizer

nltk.download("wordnet")

# Create a WordNetLemmatizer instance
lemmatizer = WordNetLemmatizer()
lemmatized_word1 = lemmatizer.lemmatize("Historical")
lemmatized_word2 = lemmatizer.lemmatize("History")

print(lemmatized_word1)
print(lemmatized_word2)
```

**Output**
```
 Historical
 History
```

## Word embeddings

It is a technique where individual words are represented as real-valued vectors in a lower-dimensional space and captures inter-word semantics.

### Types of word embeddings

Based on the technique used, word embeddings can be divided into two parts:
1. **Count or frequency** - This includes techniques such as One-Hot Encoding, Bag of Words and TF-IDF
2. **Deep Learning Trained Models** - Word2Vec (CBOW, Skipgram)