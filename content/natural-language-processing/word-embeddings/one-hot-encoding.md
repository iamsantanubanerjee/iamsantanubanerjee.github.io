---
title: "One-Hot Encoding"
description: ""
summary: ""
date: 2024-02-29T20:07:28+05:30
lastmod: 2024-03-03T12:16:48+05:30
draft: false
menu:
  natural-language-processing:
    parent: ""
    identifier: "one-hot-encoding"
weight: 3
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## What is One-Hot Encoding

Imagine we have the following document:

```python
document = "The blue bird was sitting on the tree"
```
From this document, we have a vocabulary (unique words and symbols) of **size 7** as follows:

```
 ['the', 'blue', 'bird', 'was', 'sitting', 'on', 'tree']
```

> **Notice** how every word has been converted into lower case. If not, 'The' and 'the' would be treated as seperate unique words in our vocabulary and our vocabulary size would then be 8

After establishing the vocabulary, every word is depicted as a binary vector consisting of 0s and 1s. The vector's length matches the vocabulary size, and each position in the vector corresponds to a distinct word in the vocabulary. When a specific word is found in a given text sample, its corresponding position in the vector is designated as 1, while all other positions are set to 0. This implies that each word is distinctly characterized by a binary vector, wherein only a single element is 1 (signifying its existence), and all other elements are 0.

One-Hot Encoding of the above document would look like:

```
 [1, 0, 0, 0, 0, 0, 0] --> the
 [0, 1, 0, 0, 0, 0, 0] --> blue
 [0, 0, 1, 0, 0, 0, 0] --> bird
 [0, 0, 0, 1, 0, 0, 0] --> was
 [0, 0, 0, 0, 1, 0, 0] --> sitting
 [0, 0, 0, 0, 0, 1, 0] --> on
 [0, 0, 0, 0, 0, 0, 1] --> tree
```


### Advantages

* Easy to implement
* Intuitive

### Disadvantages

* Creates sparse vectors which can be computationally expensive for large vocabularies 
* Out of Vocabulary - words not present in the training data can break the model
* Does not capture inherent relationships or semantics between words

### Example Code

```python
document = "The blue bird was sitting on the tree"

# Tokenizing the corpus into words
words = [word.lower() for word in document.split()]

vocabulary = []

# Creating a set of unique words (vocabulary)
for word in words:
    if word not in vocabulary:
        vocabulary.append(word)

# Generate one-hot encoded vectors for each word in the vocabulary
one_hot_encoded = []
for word in vocabulary:
    # Create a list of zeros with the length of the vocabulary
    encoding = [0] * len(vocabulary)

    # Get the index of the word in the vocabulary
    index = list(vocabulary).index(word)

    # Set the value at the index to 1 to indicate word presence
    encoding[index] = 1
    one_hot_encoded.append((word, encoding))

print(f"Vocabulary: {vocabulary}")
print(f"Vocabulary size: {len(vocabulary)}")

print("\nOne-hot encoded vectors:")

# Print the one-hot encoded vectors
for word, encoding in one_hot_encoded:
    print(f"{word}: {encoding}")
```

**Output**

```
 Vocabulary: ['the', 'blue', 'bird', 'was', 'sitting', 'on', 'tree']
 Vocabulary size: 7

 One-hot encoded vectors:
 the: [1, 0, 0, 0, 0, 0, 0]
 blue: [0, 1, 0, 0, 0, 0, 0]
 bird: [0, 0, 1, 0, 0, 0, 0]
 was: [0, 0, 0, 1, 0, 0, 0]
 sitting: [0, 0, 0, 0, 1, 0, 0]
 on: [0, 0, 0, 0, 0, 1, 0]
 tree: [0, 0, 0, 0, 0, 0, 1]
```
